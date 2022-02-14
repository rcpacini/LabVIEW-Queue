# LabVIEW Queue
 Queue library for LabVIEW

## Getting Started

Open and run the `/src/Demo.vi` to see an examples on how to use this Queue library in LabVIEW.

![QueueDemo](/docs/imgs/QueueDemo.png)

## Overview

This Queue library contains the malleable VI's to support multiple variations of Queues in LabVIEW. This library uses a string queue at it's core and supports the following:

Features:
- Named Queues are stored in a functional global
  - Same reference shared by separate threads
  - Obtaining and Releasing Queue references when enqueue by name no longer required
- Malleable Enqueue VI support:
  - Enum or String message data types
  - Single or multiple messages
  - Single or multiple Queue or Queue Names
- Malleable Dequeue and Preview VI's support:
  - Enum or String message data type cast
  - Timeout Enum or String message
- Malleable Flush and Status VI's support:
  - Parsing Message vs. Data
- Melleable Release support:
  - Release by Queue Reference or Queue Name (always Force Destroys)
- List all Queue Names and Queue References in memory
- Minimal ammount of code for common functionality

Rather than using the built-in queue feature, this library uses it's own functional global to avoid dangling queue refnums. If the `Obtain.vi` is called with a Queue Name, the queue reference gets cached in a functional global map look up table. Each time the Obtain is called with the same name, the same Queue reference is returned, thus eliminating the need to release the reference when calling queue methods by name.

The `Enqueue.vim`, `Dequeue.vim`, `Flush.vim`, `Status.vim` and `Release.vim` all support a Queue reference or Queue Name as an input, making the Queue VI's more versatile for multi-threaded applications

![QueueVIs](/docs/imgs/QueueVIs.png)

## Enqueue

The **Enqueue.vim** handles nearly every enqueue combination for multiple references, message data types and enqueue behaviour.

![EnqueueRefnums](/docs/imgs/EnqueueRefnums.png)

The message data types support Enum and Strings with flattened data separated by a comma `<message>,<flattened_data>`.

![EnqueueMessages](/docs/imgs/EnqueueMessages.png)

Use the built-in `Unflatten From String.vi` to convert the data back to the native data type.

## Dequeue

The **Dequeue.vim** supports an Enum or String `Message Type` input to type case the message output. This is useful to strictly type case structures. Specify the `Timeout Message` to avoid nested case structures to handle the timed out condition.

## Testing

To Do...
---
layout: post
title: Announcing trunkline 1.0.0-alpha!
---

Today we're excited to announce the release of our first alpha build for [trunkline](https://github.com/rtc-dialtone/trunkline) - a batteries included multi-protocol WebRtc communications backend. 📶🔋

![trunkline logo](https://github.com/rtc-dialtone/trunkline/raw/master/.github/logo.png)

Trunkline was created to help create scale-able WebRTC backends, that facilitate communication between many peers. It's goal is to be simple, easy to understand, and configurable. Today trunkline supports `http` as an underlying protocol, and in-`memory` databases. As we work toward a `1.0.0` release, you can expect to find `sql` databases and the `raw-socket` protocol to be functional as well. We'll also have a pattern for optionally securing communications over the wire, as well.

Before we can talk about the specifics of how trunkline works, we must first introduce some concepts.

## New Concepts

> Note: To quickly view these concepts in use, see [the OpenAPI doc visualizer](https://redocly.github.io/redoc/?url=https://raw.githubusercontent.com/rtc-dialtone/trunkline/master/src/lib/protocols/http-swagger.yml&nocors).

Trunkline operates on a concept of peers, features, and messages. Messages are just small pieces of data (represented as strings) and some metadata about who sent them, when they were created, etc. Peers are WebRTC enabled clients, that are uniquely identified in the system, and are capable of sending and receiving messages. Finally, peers have a concept of features - string representations of their capabilities and interests.

Peers and messages should feel pretty natural - you can use them to identify and communicate with others. However, features may seem a bit nebulous - let's dive deeper. 

There are a few common patterns we see in WebRTC enabled apps. There's apps that create a 1:1 audio/video connection (Skype video calls), there's apps that create 1:many audio/video connections (Google Hangouts), and there's apps that do something unique. However, we've found that most scenarios can be accomplished by storing index-able data associated with peers. Want to setup a 1:many channel? Great - add some feature data identifying a room, and connect to all other peers with that data. Want to setup some complex service discovery system? Great, give all services the same feature data, and have clients select one peer that has that data.

To summarize - Peers have index-able feature data to help with discoverability, and they can send messages to each-other to communicate.

## Getting started

For now, [trunkline](https://github.com/rtc-dialtone/trunkline) is still in the `alpha` phase. It's more than likely that you'll run into bugs - If you do, please [file them here](https://github.com/rtc-dialtone/trunkline/issues).

To install trunkline's latest release and learn how to configure and use it, please see [the trunkline readme](https://github.com/rtc-dialtone/trunkline#quickstart).

Thanks for reading - We're looking forward to sharing more great things soon.
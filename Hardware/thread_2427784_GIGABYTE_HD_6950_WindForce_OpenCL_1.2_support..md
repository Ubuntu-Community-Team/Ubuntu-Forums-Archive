---
title: "GIGABYTE HD 6950 WindForce OpenCL 1.2 support."
date: 2019-09-26
forum: Hardware
---

### Post by mcslk27 on 2019-09-26
Hello everyone, hope you have great day. I'd like to present to you my issue. 

Yesterday I tried to run gpu acceleration on Keras by PlaidML backend, I installed framework on my virtualenv and clinfo says that OpenCL version = 1.1. 
PlaidML requires 1.2 version and it results that GPU can't be used to accelerate computing. 

Net info says that my GPU support OpenCL 1.2: [https://www.techpowerup.com/gpu-specs/gigabyte-hd-6950-windforce-3x-oc-1-gb.b1252](https://www.techpowerup.com/gpu-specs/gigabyte-hd-6950-windforce-3x-oc-1-gb.b1252)

Is it caused by some AMD drivers or OpenCl drivers incompatibility?

I'm using Ubuntu 18.04.

Greetings, Marcin.

---

### Post by Yellow Pasque on 2019-09-26
I don't think it's possible. libclc only supports 1.1

---


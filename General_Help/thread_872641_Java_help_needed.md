---
title: "Java help needed"
date: 2008-07-28
forum: General Help
---

### Post by Cloudedbrains on 2008-07-28
I cant get Java 2 install on 8.04 Ubuntu

Have tried add/remove and synaptic but no go

How do I get it too install

---

### Post by dexter.deepak on 2008-07-28
its better you tell us the error messsage you received.
for the moment, try this and tell me if you get any error message
open up a  terminal and type;
1. for sun's jdk:(i assume you want jdk6)
```
sudo apt-get install sun-java6-jdk
```
for sun's jre:
```
sudo apt-get install sun-java6-jre
```

you can also try gcj, which is faster, but gives platform dependent code:
```
sudo apt-get install gcj
```
for openjdk/jre:
```
sudo apt-get install openjdk-6-jdk
```
or
```
sudo apt-get install openjdk-6-jre
```

---


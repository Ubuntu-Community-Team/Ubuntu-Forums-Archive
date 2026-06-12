---
title: "android ... buffer overflow help"
date: 2011-02-26
forum: Hardware
---

### Post by zero7404 on 2011-02-26
i am doing a dmesg on my phone (android 2.2) to see the syslog and i spotted several buffer overflow messages that start with evdev and then event1-xxxx, where xxxx is 4 digits. i assume these digits are associated with a driver that is having memory allocation issues.

is anyone knowledgable with how to figure out what the numbers mean, so that i can find out what is causing the problem ? is there a command i can issue in the terminal to look up the event id's that correspond to the log output and what service/app they are originating from ?

buffer overflows lead to venerabilities which can be exploited. so i want to try and minimize this.

---

### Post by zero7404 on 2011-02-27
does anyone know how i can identify an event id that's associated with a buffer overflow message in the system logs ?

---


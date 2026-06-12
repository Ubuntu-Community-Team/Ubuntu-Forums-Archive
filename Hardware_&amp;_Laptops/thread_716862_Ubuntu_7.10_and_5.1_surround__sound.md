---
title: "Ubuntu 7.10 and 5.1 surround  sound"
date: 2008-03-06
forum: Hardware &amp; Laptops
---

### Post by residentevil on 2008-03-06
Hello, i'm writhing you about some very interesting problem with my Ubuntu 7.10.
I have an audio system (5.1) and i use .asoundrc file to duplicate the signal, but i cant use more then one app which use sound when i want to listen to music using amarok and mplayer it doesn't work or ant to use my microphone and amarok  together. I want to know is there any way to escape from this problem ?
the .aosoundrc file is :
ren@UmBrELlaCorp2008:~$ cat .asoundrc 
pcm.!default {
   type plug
   slave.pcm "surround51"
   slave.channels 6
   route_policy duplicate
}

---


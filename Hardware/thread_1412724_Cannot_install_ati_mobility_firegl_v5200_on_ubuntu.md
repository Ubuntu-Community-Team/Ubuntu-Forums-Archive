---
title: "Cannot install ati mobility firegl v5200 on ubuntu 10.04"
date: 2010-02-21
forum: Hardware
---

### Post by cllesko15 on 2010-02-21
Hi guys,

I am a total noob with Linux, but I have just installed Ubuntu 10.04 and am trying to make it recognize my video card. 
I have a HP Compaq nw8440 with Ati Mobility FireGL v5200 and from what I concluded it seems that xserver is what ubuntu is using for my video.
I downloaded xorg-edit but am not sure how to add the graphics card since i dont know the bus id etc. does anybody have any suggestions?
The reason I want to make ubuntu recognize my video card is the fact that any games or videos that I play are choppy and have lines going through them witch rapid camera movement. Any help would be greatly appreciated.

- Chris

---

### Post by mosibfu on 2010-03-06
ok this is kind of quick and dirty

ubuntu 10.04 is still in alpha phase, it uses xorg 7,5  the ati driver doesnt support xorg 7,5 yet.. so there is no ati driver for 10.04

i think ubuntu 10.04 releases the 29th, by then i hope there will be a beta ati driver availible. there was the same problem with 9.10 alpha i believe.. so for now, use the open souce driver for 2d acceleration in 10.04, or reinstall 9.10 ..

-mosibfu

---

### Post by nc_jed on 2010-04-19
> **cllesko15 said:**
> Hi guys,

I am a total noob with Linux, but I have just installed Ubuntu 10.04 and am trying to make it recognize my video card. 
I have a HP Compaq nw8440 with Ati Mobility FireGL v5200 and from what I concluded it seems that xserver is what ubuntu is using for my video.
I downloaded xorg-edit but am not sure how to add the graphics card since i dont know the bus id etc. does anybody have any suggestions?
The reason I want to make ubuntu recognize my video card is the fact that any games or videos that I play are choppy and have lines going through them witch rapid camera movement. Any help would be greatly appreciated.

- Chris

Same machine/card/specs, etc.  9.10 works perfectly.  Course, I was never a bleeding edge kinda guy.

---


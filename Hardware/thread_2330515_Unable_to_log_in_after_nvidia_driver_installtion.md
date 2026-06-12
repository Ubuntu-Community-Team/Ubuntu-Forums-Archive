---
title: "Unable to log in after nvidia driver installtion"
date: 2016-07-12
forum: Hardware
---

### Post by ChronicUser on 2016-07-12
Hi

This seams to be a recurring issue. 
I installed the nvidia drivers on my ubuntu box and then I am unable to log in via GUI ctrl+alt+f1 log in works just fine.

Here is my setup:

Fedora 23 host
KVM Ubuntu Guest 
Nvidia asus gtx 970

My computer has 3 graphics cards one is AMD firepro w600 which is used by the host system and the other two are
asus strix gtx 970.

I also have ovmf set up for the virtual machines.

So I have installed ubuntu as a VM and passes the 2 nvidia GPUs it boots just fine and after the installtion of nvidia drivers from the repos I am unable to log in.

You might argue that this is a KVM problem but that is what I though as well, however I do believe that I have eliminated this possibility as there are 5 virtual machines running with GPU pass-through working just fine.
And after reading previous posts on the subject I came to a conclusion that this is specific to ubuntu.

I did try removing the .Xauthority did not help

when I run dkms status 

bbswitch, 0.8, 4.4.0-28-generic, x86_64: installed
nvidia-361, 361.42, 4.4.0-28-generic, x86_64: installed

Could anyone shed some light on the matter.

---


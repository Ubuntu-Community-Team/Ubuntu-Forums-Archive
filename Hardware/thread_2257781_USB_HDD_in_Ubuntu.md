---
title: "USB HDD in Ubuntu"
date: 2014-12-22
forum: Hardware
---

### Post by Christian_Schuster on 2014-12-22
Hi Folks,

I am absolutly new with unbuntu and I only Need to copy some files from 2 HDD's to another HDD. Well my Synology NAS Station got an error and they write that i should build in my 2 HDDs in a PC and install  **lvm2** with the command **root@ubuntu:~$ apt-get install lvm2. **After that I should use the following command: [B]root@ubuntu:~$ mdadm –Asf && vgchange -ay.

[/B]The complete article to recover my data can be found there: [https://www.synology.com/en-global/knowledgebase/faq/579](https://www.synology.com/en-global/knowledgebase/faq/579)My Problem is that I have no PC where I can install These 2 HDD's. My PC is too old and cannot use SATA HDD's, usualy I use a notebook Do you have any idea whether I can connect my two HDD's via USB HDD Boxes and use These commands? Sorry but I would Need a detailed Explanation as of I am not familiar with that OS.

Thank's to those who help.

Chris

---

### Post by weatherman2 on 2014-12-22
If you can connect both hard drives via SATA to USB adapters or enclosures - two of them, so you can connect both drives at the same time - then yes, it should work.

If you can find a slightly newer PC with SATA ports, though, it might be easier/cheaper.  PC motherboards have had SATA ports for about ten years.  You can also buy a PCI card to add SATA ports to an old PC - but finding a PC 10 years old or newer that has SATA ports might be best.

---

### Post by mörgæs on 2014-12-22
In general it's not recommended to enable the root account:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---


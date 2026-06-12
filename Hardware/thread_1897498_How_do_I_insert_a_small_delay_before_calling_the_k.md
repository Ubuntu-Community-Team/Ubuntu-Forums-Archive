---
title: "How do I insert a small delay before calling the kernel?"
date: 2011-12-19
forum: Hardware
---

### Post by ZootNerper on 2011-12-19
Hi folks,

I want to insert a small delay before the kernel is called at boot (not a Grub menu selection delay)

Could someone please tell me which file to edit and also the delay command itself.

Thanks

---

### Post by ZootNerper on 2011-12-19
OK, may have got this wrong. When the kernel is called it runs a load of commands as it starts this or that service. These are what you see if "quiet splash" is not used.

I think, I can insert a delay between one command and the next (I only need to do it once).

But I don't know the file or the command.

Hopefully, I remembered a bit better this time.

(I have a Acer Aspire One 522 with C60 APU, with the latest Catalyst drivers. It will freeze on booting into Ubuntu and I read somewhere that taking out "quiet splash" and inserting a delay into the boot sequence would prevent this. But for the life of me, I can't find the web page I read :}  )

---

### Post by oldfred on 2011-12-19
I am not sure this is the command you are looking for?

quiet splash vt.handoff=7 [COLOR=Red]rootdelay=90 
[/COLOR] 
You can test it by use e on the grub menu and typing it in. But it is only for that one boot.

gksudo gedit /etc/default/grub
# after any change:
sudo update-grub
[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)
> GRUB_CMDLINE_LINUX
    * Entries on this line are added to the end of the 'linux' command line (GRUB legacy's "kernel" line) for both normal and recovery modes. It is used to pass options to the kernel. 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
   * This line imports any entries to the end of the 'linux' line (GRUB legacy's "kernel" line). The entries are appended to the end of the normal mode only.
       o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". 



---

### Post by ZootNerper on 2011-12-21
Thanks Oldfred. Not quite what I meant, but can't find what I want either.

Oh well. Thanks for your post

---

### Post by oldfred on 2011-12-21
That was not a grub command but a parameter passed to the kernel at boot time by grub.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

---


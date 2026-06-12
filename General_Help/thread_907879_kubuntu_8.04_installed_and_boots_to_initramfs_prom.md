---
title: "kubuntu 8.04 installed and boots to initramfs prompt"
date: 2008-09-01
forum: General Help
---

### Post by Hagood on 2008-09-01
Tuffy, I had Gusty running for quit awhile and have my mail server, web server and many programs and data on what I call my Linux machine. Thinking I was smart and going to update to Hardy I used the version update button.  Everything went smooth and there was no errors. when it finished it said complete and press this button to reboot.  Great, I thought, That was the last I saw of Kubuntu.  My computer boots to a (initramfs) prompt with what is a limited shell that ls shows just a basic Linux directory. 

I have Googled my heart out and can find no useful information. That is, useful for me.  Most info I found similar is people booting from a live CD. I can boot from the cd but not from my mew installation of Hardy. 

If you take on the challenge, I thank you.

Rex

A suggestion of pressing Esc got me to the Boot menu and I could boot from a different Kernel.  I booted to Hardy. Now I need to fix my Boot menu so I have the right Kernel at the top. Any help I get will be appreciated. 

Thanks,

Rex

---

### Post by Washer on 2008-09-06
er.. edit grub from your livecd?

---

### Post by kentbower on 2008-09-07
Your situation is *not* like mine, except that I also couldn't boot because of the initramfs prompt.

But this might be worth a try in WinXP because it couldn't hurt (assuming c: is your hard drive with ubuntu):

**chkdsk c: /f**

(you may need to 'schedule' the chkdsk and reboot windows)

That finally fixed my initramfs problem that happened after my laptop ran out of battery while ubuntu was running.

I was getting:
ALERT! /host/ubuntu/disk/root.disk does not exist

and then the 

initramfs_ prompt

---


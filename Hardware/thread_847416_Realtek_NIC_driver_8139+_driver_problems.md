---
title: "Realtek NIC driver 8139+ driver problems"
date: 2008-07-02
forum: Hardware
---

### Post by tommyj55 on 2008-07-02
When ubuntu tries to boot, it fails on the Realtexk 8139+ NIC card.  The message says I should use driver 8139too instead of 8139cp.

Ive tried using the hwinfo --netcard, rmmod 8139cp, and modprobe 8139too commands, but I must not be at the proper command prompt, because hwinfo is not recognized at the prompt, and the rmmod and modprobe commands are ignored.

First - I'm attempting to install 7.10 - Is this driver problem corrected in 8.04?

If not, I could use some assistance in rectifying the problem. I have my PC set up with EasyBSD, so I can dual-boot between Vista and Ubuntu.  I'm somewhat of a newbie to ubuntu and Linux.  How do I get to the correct prompt to use the above commands?

Thanks,

TJ

---

### Post by pytheas22 on 2008-07-02
How far into boot are you getting before it fails?  Have you installed Ubuntu to hard disk (if so, did the live CD boot alright?) or are you just trying and failing to boot to the CD?

Also I don't know what hwinfo is.  It sounds like maybe a BSD program.  What you want to use on Ubuntu is:
```

lshw -C Network
```

or:
```

lspci
```

And the modprobe commands won't necessarily give any output unless an error occurs.  Try running with the --verbose option.  You may in fact be at the right command prompt and just don't realize it.  If that's the case, then running the command:

```
sudo -s
echo 'blacklist 8139cp' >> /etc/modprobe.d/blacklist
```

and rebooting would probably solve the problem altogether.

If not, if you do have Ubuntu on your hard drive, another solution would be to either remove the network card or disable it in BIOS, if possible, and then boot into Ubuntu normally.

A third approach is to mount the Ubuntu file system under Windows or BSD and move or delete the 8139cp module.  It should be located at /lib/modules/[your kernel version]/kernel/drivers/net/.  Keep in mind that if you have more than one kernel installed, there will be a copy of 8139cp.ko for each kernel.

If you're trying to boot to the live CD but are unable because of this problem, you could edit the ISO file to remove 8139cp.ko.  I think that Archive Manager in Ubuntu can do that, and I know of a few Windows programs that can as well.

As for the problem being solved in Hardy: there's a good chance that it is.  Do you know the exact chipset of your card or its lspci entry?  If so, some quick Googling would probably answer the question.

---


---
title: "Broken ram and memmap kernel parameter"
date: 2008-07-15
forum: Hardware
---

### Post by grasnal on 2008-07-15
Hi. I'm using broken ram module - DDR 512 pc3200. Generaly it's ok but sometimes system fail to start or crash during normal use.

I readed about memmap and BadRam but dont't have idea how to use it.

Memtest shows that bad address is '0001d35c894' and this is at 467,7 MB of my ram module.

And here is my question:

How to use memmap exclude option to disable kernel of using this part of RAM? I know that this is kernel parameter described here: [>>click<<]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;f=Documentation/kernel-parameters.txt;h=508e2a2c98644ad6c4ee70e59a33191af9af541e;hb=1312848e92a0686cb5124aa86ea58d55ba795742") but i don't know how to run my ubuntu with this?
I should compile new kernel or set this parameter somewhere?

And what is all about BadRam? Few links i have found at google said that this is something in 2.6.25 kernel or there is patch to insert this in to the kernel [>>here<<]("http://rick.vanrein.org/linux/badram/") and [>>here<<]("https://help.ubuntu.com/community/BadRAM")

Generally if anybody have idea how to block access to invalid ram address I'll be very grateful for posting this here.

TIA

P.S.
I'm using Ubuntu 8.04 with kernel 2.6.24-19-generic
I'm sorry for my English but it's not my native language.

---

### Post by dinub1 on 2008-07-15
> **grasnal said:**
> Hi. I'm using broken ram module - DDR 512 pc3200. Generaly it's ok but sometimes system fail to start or crash during normal use.

I readed about memmap and BadRam but dont't have idea how to use it.

Memtest shows that bad address is '0001d35c894' and this is at 467,7 MB of my ram module.

And here is my question:

How to use memmap exclude option to disable kernel of using this part of RAM? I know that this is kernel parameter described here: [>>click<<]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;f=Documentation/kernel-parameters.txt;h=508e2a2c98644ad6c4ee70e59a33191af9af541e;hb=1312848e92a0686cb5124aa86ea58d55ba795742") but i don't know how to run my ubuntu with this?
I should compile new kernel or set this parameter somewhere?

And what is all about BadRam? Few links i have found at google said that this is something in 2.6.25 kernel or there is patch to insert this in to the kernel [>>here<<]("http://rick.vanrein.org/linux/badram/") and [>>here<<]("https://help.ubuntu.com/community/BadRAM")

Generally if anybody have idea how to block access to invalid ram address I'll be very grateful for posting this here.

TIA

P.S.
I'm using Ubuntu 8.04 with kernel 2.6.24-19-generic
I'm sorry for my English but it's not my native language.

:) You are apparently looking for challenges in life... I do not know why complicate yourself. Couldn't you simply buy a RAM chip and replace the damaged one?

---

### Post by grasnal on 2008-07-16
@dinub1:

I can... but if it's only a matter of hour or two and occasion to learn something why should I pay ~15 euro for nothing? I's only one bad address there and theoretically it can be masked/blocked so my question still as above - how can I achieve that?

---

### Post by dinub1 on 2008-07-16
> **grasnal said:**
> @dinub1:

I can... but if it's only a matter of hour or two and occasion to learn something why should I pay ~15 euro for nothing? I's only one bad address there and theoretically it can be masked/blocked so my question still as above - how can I achieve that?

Well, theoretically you could do many things... but in practice...
I am not sure if what you are asking is not hard to do and if it worths it.... be aware that memory can go worse... and that may fail you more...
I do not know how you can achieve marking/excluding a block of memory in Linux.

---

### Post by dinub1 on 2008-07-16
OK... Here is what I found... try to look into it.

[http://badmem.sourceforge.net/docu/BadMEM-HOWTO.html](http://badmem.sourceforge.net/docu/BadMEM-HOWTO.html)

Good luck!

---

### Post by grasnal on 2008-07-18
@dinub1:

Thanks for that. Work in progress ;).

If anyone can tell me sth about memmap usage here is the place ;).

---

### Post by evets25 on 2008-07-18
No, don't go there, just replace the ram. Once a stick of ram starts to die, it will continue to die a slow and painful death. Even if you ARE able to block out those sections of the ram, it would 

A) confuse the hell out of your OS
B) continue to fail in *different* parts of the ram. 

It would be like trying to use a broken bucket to bail water out of a boat, while new holes are appearing in both your bucket and your boat. It just won't work. I speak from experience here when I say it's just not worth it to use bad ram. Just replace it and you'll save yourself some major headaches.

---

### Post by grasnal on 2008-07-19
@evets25:

Thank you for your warning but this is not as critical as you see it. I know how the broken ram can mess up mu OS but i want to learn something.

This 512 MB chip is not in usage now.

So, any help at this topic?

---

### Post by pdwhittaker on 2009-05-05
Don't know if you're still trying to do this, but this might help if you are.  I haven't tried this myself, but it should give you the pointers you need.

Bear in mind that (as others have said) replacing bad ram is better than trying to work around it.  On the other hand, you may not be able to find replacement ram if your system is very old, for example, or you may just be curious.

Looking at the link you provided in your original post, I found the following section that is relevant to your problem:

```

1130         memmap=nn[KMG]$ss[KMG]
1131                         [KNL,ACPI] Mark specific memory as reserved.
1132                         Region of memory to be used, from ss to ss+nn.
1133                         Example: Exclude memory from 0x18690000-0x1869ffff
1134                                  memmap=64K$0x18690000
1135                                  or
1136                                  memmap=0x10000$0x18690000

```

We'll use this parameter to mark the bad area as "reserved" so that it doesn't get used by the kernel.  Your bad address is at 0x0001d35c894 (that's in hexadecimal) which is a little more than 467*1024*1024 (i.e. 467M).  We could use either form of the address, but we'll use the short one.  To make sure we catch the bad bits, we'll remove a whole megabyte, starting at 467M.  So the first number is 1M and the second number is 467M.  (The examples in the documentation always have hex for the second number, but the first line says you can use K, M, or G there too.  467M is 0x1d300000 if you find you need it.)  This gives us

```
memmap=1M$467M
```

Now we've got that, we just need to pass it to the kernel.  This has been covered in detail at [https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions"), in the section "Change Boot Options Permanently On An Existing Installation".

To recap the details there, you change kernel options by updating the file /boot/grub/menu.lst.  It doesn't hurt to make a backup before you change it, too.  There are two different approaches.  You can add "memmap=1M$467M" (no quotes) to the end of just one specific kernel line - look for the "title" line that matches the grub menu entry that you select, and change the "kernel" line that comes right after it.  With this option, you only need to save the file and reboot for it to work, but next time something runs update-grub it looks like you might lose the changes you made.  (One thing to make sure of is that your editor doesn't break your line in two when you add the extra text to the end of it.  If it does, use backspace to remove the linebreak.)  Alternatively, you can look for the "# kopt=..." line, add "memmap=1M$467M" to the end of that, and then run update-grub.  This will update the options for all of the kernels, and won't go away if update-grub runs again.

Personally, I'd use the first method until it looks like it's working okay, and then perhaps use the second one to make it stick.  If you don't mind the extra typing, you could also follow the "Changing Boot Options Temporarily" steps on the same page - again, just add the "memmap=..." part to the end.

That should be it.  If you run the "free -m" command before and after changing the kernel parameters, you might (I can't confirm this) find that the total goes down by one when the kernel option is active.

If you do try this out, post back here and share your findings.

---

### Post by dbutcher on 2009-09-11
Not trying to hijack the thread, but I had a similar problem as grasnal (a single memory chip, memtest reports a failing address, and I'd rather try to fix it than just buy a new chip).

I followed the instructions by pdwhittaker (thanks!), adding memmap=1M$21M (in my case) to the kernel line in /boot/grub/menu.lst

I can confirm that "free -m" does show the total memory reduced by 1

I don't yet know if blocking out this section of ram will fix my system flakiness (so far, so good, fingers crossed, etc.), but I thought I would report findings so far in case others stumble across this thread as I did.  

Cheers,
Dave

---

### Post by akelm on 2010-05-29
I successfully used the method provided by pdwhittaker (thanks!).  In my case, there were two bad memory addresses, and so I used the memmap kernel parameter twice, once for each bad address.  I confirmed that this resulted in a reduction of 2 MB in free memory.

---

### Post by sotirovlyu on 2010-06-25
I also did disabling of some regions of memory which are failing. 

To all members suggesting to buy new memory, remember that there are notebooks (may be even desktops.. ) with onboard memory, that you cannot remove/exchange easily.

---

### Post by naugtur on 2010-10-26
> To all members suggesting to buy new memory, remember that there are notebooks (may be even desktops.. ) with onboard memory, that you cannot remove/exchange easily.And there are old PCs that one might want to use for some tasks, but investing money in new ram for them... you know.


Now my question: How do I lock multiple separate spaces? Can I put two memmap parameters? Or is there an additional syntax?

[edit] And I found the answer. Yes, you can provice multiple "memmap=..." bits.

---

### Post by psychydyl on 2010-12-30
Hi! On Meerkat, adding memmap=2M$2824M to the kernel line in grub just reboots the system. So at the moment I'm using mem=2824M and wasting more than a GB of RAM. Why isn't memmap working here?

---

### Post by AgentBSMITH on 2012-05-22
Probably an old topic, but with Google I stumbled upon this so I guess many others will do too.
To give a reply on the constant reboot (or hanging on reboot) problem, is that you cannot use memmap=2M$2824M without putting a backslash (\) in front of the $.
So you should use memmap=2M\$2824M or if you edit this in grub2 where it has the double quotes (if you do not change it to single quotes) you need to give an extra backslash for the backslash as this : memmap=2M\\\$2824M

(source : [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/448413](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/448413))

I hope this helps other visiting people.


Have a nice day !

---


---
title: "demo stops loading"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by whitedog on 2009-02-02
ok i got the demo and it loads when i start up, but then this appears

0.416026 MP-BIOS BUG:8254 timer not connected to 10-apic
Loading please wait....

BusyBoy v1.10.2 (ubuntu 1:1.10.2-1ubuntu6) built in shel (ash)
Enter 'help' for a list of built in commands.

(initramfs)


ive entered help but idt that has to do with the solution, as well as i cant understand what the commands are. 

Can anyone help me?

---

### Post by tommcd on 2009-02-03
> **whitedog said:**
> ok i got the demo and it loads when i start up, but then this appears


By "demo" I assume you mean the Ubuntu 8.10 live CD, is that correct?

The first thing you need to do is rule out a corrupted Ubuntu CD. How did you burn the CD? Try burning the CD with Iso Recorder or Infra Recorder if you are burning it from Windows:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
And be sure to burn at the slowest possible speed. Then when you boot the CD choose the option to check the CD for defects. If the CD checks out ok then proceed to boot the CD to get to the Ubuntu desktop.

And welcome to the Ubuntu forums!

---

### Post by whitedog on 2009-02-03
i used this method at a very low burn speed, about 1/4th of what my max is and still got the same error....

this is bugging me because i rly want ubuntu instead of vista which is what i currently have.

any new advice? help is much apreciated!

---

### Post by tommcd on 2009-02-04
Did you try the option to check the CD for defects when the Ubuntu CD boots up? Did it report that the CD was ok?

---

### Post by whitedog on 2009-02-04
i never get to that point.

i start up and it asks me if i wana use windows or ubuntu, i choose ubuntu and it loads like it should, then after a minute or two it finish's and then the above appears.

---

### Post by avtolle on 2009-02-04
It appears to me from the above that you already have Ubuntu installed, given your choice of Windows or Ubuntu on start-up. If so, how did you install it? Is this a Wubi install?

---

### Post by Rudedawg on 2009-02-04
This is a link to an epic 34 page thread about a similar issue. 

[http://ubuntuforums.org/showthread.php?t=765195&highlight=i%2Fo+buffer+error+fd0]("http://ubuntuforums.org/showthread.php?t=765195&highlight=i%2Fo+buffer+error+fd0") 

The long and short of it is to add: 

"all_generic_ide floppy=off irqpoll" 

Without the quotes to the end of the text line that pops up when you press the boot option (f6) of the live cd menu and then once installed, it needs to be added into GRUB to boot correctly. There is tons more info in the thread above. I'm not sure if it works, but I have been researching the issue since I'm having a similar problem. I'll be trying this fix when I get home tonight. Good Luck!

---

### Post by Rudedawg on 2009-02-04
BTW, It is not a disk burning error or a cd defect error (although it does seem like it could be). This error will probably pop up regardless of which choice you choose from the live cd menu (even choosing memtest and check cd for defects will pop this error up). This is a very common problem right now. If you have already installed ubuntu, just follow the directions in the thread above to modify GRUB so that your box will boot into ubuntu properly. 

for fun, google "initramfs ubuntu" just to see how many people are having similar issues. 

Hope this info helps.

---

### Post by whitedog on 2009-02-04
"all_generic_ide floppy=off irqpoll" worked thanks ^_^

i now have ubuntu up and running on my computer :)

---


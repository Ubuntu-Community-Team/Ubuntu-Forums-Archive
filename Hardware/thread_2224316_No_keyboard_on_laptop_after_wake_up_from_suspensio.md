---
title: "No keyboard on laptop after wake up from suspension"
date: 2014-05-15
forum: Hardware
---

### Post by eotakos on 2014-05-15
Hello,

So the discription of the problem is the following: 

I have a laptop that the keyboard would not wake up from suspension.  (Sony vaio vgn-cs11z is my laptop, but this fix might work for others too according to my search). So the keyboard would work just fine after booting in, but coming back from a suspension, only the trackpad would work, not the keyboard. Plugging in an external usb keyboard would also work fine, no problem. This way you're restricting the mobility of the laptop though... 

Yesterday I found a fix for this problem after several searches and attempts and failures in the past, and I thought I should share. Here's how:

The source of the problem is the i8042 controller which has the ps/2 keyboard connected on it. This controller is not very well supported by the kernels, so it needs some twicking to get over the problem in question.

First to make sure that this fix would have some chances working for you too, check that your laptop uses this controller by running
```
dmesg | grep i8042
```

Here's what I get, so you'd expect to see something equivalent:
> 
[    1.514469] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    1.525273] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.525287] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.526035] input: AT Raw Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[   21.927438] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10


Now, to TRY and see if this fix works for you:
Reboot, and bring up the grub menu. Highlight the option that you're running and press 'e', to edit the entry. Go down to the line that says 'linux...' and has the name of the kernel right next to it. Go to the end of the line, and add
```
i8042.direct i8042.dumbkbd
```

These are the options we are passing to the kernel. These particular options are the ones that worked for me (namely my sony vaio laptop). If you have a different laptop that uses the same i8042 controller, maybe some other options would do the trick. Here is a list with some more options you could try (or whatever combinations of them). This page gives also a discription of what each of the options does:
[http://lightrush.ndoytchev.com/random-1/i8042quirkoptions](http://lightrush.ndoytchev.com/random-1/i8042quirkoptions)

After you put in your options/parameters, press 'f10' to continue with booting up the kernel with your new options. Then, try hybernating and waking up, to see if your keyboard now works. If it does, you can go on and make this change permanent:

First, see which kernel you're running (in case you don't remember from what you just did before). 
```
uname -a
```

Then, edit /boot/grub/grub.cfg with the text editor you're using. Example:
```
gedit /boot/grub/grub.cfg
```

Find that line which starts with "linux..." and has the name of the kernel right next to it. Go to the end of the line as before, add your parameters/options, save the file, and exit. That would be it. Next time you boot up, the parameters are passed to the kernel, and your keyboard should wake up.

Note: This fix was not something that I came up with, since I have limited/no knowledge of kernel twicking. So it's only fair that I give you here the posts/links that lead me to the answer. Also, if this fix doesn't work for you, you can try experimenting with solutions that are proposed therein. You already have the link with the options you can pass (I don't know if they're all the options, but they're quite some :) ). Here are the others:

[https://bugzilla.kernel.org/show_bug.cgi?id=13159](https://bugzilla.kernel.org/show_bug.cgi?id=13159)
[https://bugzilla.redhat.com/show_bug.cgi?id=490250](https://bugzilla.redhat.com/show_bug.cgi?id=490250)

Anyway, I hope the fix works for you, or if not, that at least gives you a good lead.

Cheers

---


---
title: "Reloading USB + WACOM?"
date: 2008-11-10
forum: Hardware
---

### Post by srilyk on 2008-11-10
Hi,

I'm fairly sure this is a standard problem, and only mildly annoying. However, it would be awesome if there were a solution to my problem. I have a Wacom Graphire 4 USB, and when I'm booted up, if I plug it in before logging in, no problem. If I'm logged in and plug it in, I have to restart X and it works.

I just tried tail -f /var/log/messages and unplugged the wacom, and this is the output:

```
Nov 10 12:16:36 the-lappy kernel: [  614.393788] usb 2-1: USB disconnect, address 2
Nov 10 12:16:40 the-lappy kernel: [  618.585855] usb 2-1: new low speed USB device using ohci_hcd and address 3
Nov 10 12:16:40 the-lappy kernel: [  618.795463] usb 2-1: configuration #1 chosen from 1 choice
Nov 10 12:16:40 the-lappy kernel: [  618.797477] input: Wacom Graphire4 6x8 as /devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1:1.0/input/input10
Nov 10 12:16:40 the-lappy logger: device input10 is bound to the driver
Nov 10 12:16:40 the-lappy logger: must rebind
```

Is there a way to... I guess rebind the driver?

I'm about to play with a few other situations: such as when I hibernate, start up, and then plug in the tablet. On those occasions even restarting X won't help, I have to restart the entire computer.

Thanks for any help!

Edit: Ok, after a restart of X, these are the new lines that appeared in /var/log/messages:
```
Nov 10 12:26:06 the-lappy kernel: [ 1183.956826] [fglrx] interrupt source 20008000 successfully disabled!
Nov 10 12:26:06 the-lappy kernel: [ 1183.956834] [fglrx] enable ID = 0x00000000
Nov 10 12:26:06 the-lappy kernel: [ 1183.956839] [fglrx] Receive disable interrupt message with irqEnableMask: 20008000; dwIRQEnableId: 00000004
Nov 10 12:26:09 the-lappy kernel: [ 1186.492817] [fglrx] PCIe has already been initialized. Reinitializing ...
Nov 10 12:26:09 the-lappy kernel: [ 1186.503208] [fglrx] GART Table is not in FRAME_BUFFER range 
Nov 10 12:26:09 the-lappy kernel: [ 1186.503220] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
Nov 10 12:26:09 the-lappy kernel: [ 1186.503223] [fglrx] Reserve Block - 1 offset =  0X7ff5000 length = 0Xb000
Nov 10 12:26:09 the-lappy kernel: [ 1186.650795] [fglrx] interrupt source 20008000 successfully enabled
Nov 10 12:26:09 the-lappy kernel: [ 1186.650806] [fglrx] enable ID = 0x00000004
Nov 10 12:26:09 the-lappy kernel: [ 1186.651091] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000

```

And after hibernating, starting up, and plugging the tablet back in:
```

Nov 10 12:33:31 the-lappy kernel: [   97.113924] usb 2-1: new low speed USB device using ohci_hcd and address 4
Nov 10 12:33:31 the-lappy kernel: [   97.217459] usb 2-1: configuration #1 chosen from 1 choice
Nov 10 12:33:31 the-lappy kernel: [   97.218465] input: Wacom Graphire4 6x8 as /devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1:1.0/input/input11
Nov 10 12:33:31 the-lappy logger: device input11 is bound to the driver
Nov 10 12:33:31 the-lappy logger: must rebind

```

---

### Post by srilyk on 2008-11-20
Well, for anyone with a wacom who cares, I've discovered part of the solution!

If you hibernate and don't plug your wacom in on restart you can at least get it running without rebooting (at least I did). Just follow these simple steps:

1) Open a terminal window (or maybe even a run dialog).
2) type "lsusb" and hit enter
3) the little (blue in my case) light on your wacom should turn on
4) save all your programs
5) hit ctrl+alt+backspace to restart X
6) Enjoy! Your tablet should now work fine.
7) :guitar: Rock with your tablet out!

If I discover a way to get absolute mode working without restarting X I'll be sure to post that here!

Hope this helps someone besides me!

---

### Post by spupy on 2008-11-25
Hi, I'm not using Ubuntu now, but I have the same problem with my Wacom Bamboo on Gentoo. I must restart X in order to make it work.
Then I run this script that configures the tablet further:
```
#set mode to "absolute"
xsetwacom set stylus mode absolute

#set scrolling with ring
xsetwacom set pad RelWUp "key core pgdn" 
xsetwacom set pad RelWDn "key core pgup"

#set zoom with ring
# xsetwacom set pad AbsWUp "core key -" 
# xsetwacom set pad AbsWDn "core key +"

# Button <  set to + (Zoom in)
xsetwacom set pad Button1 "core key +"
# Button FN1  set to - (Zoom out)
xsetwacom set pad Button2 "core key -"
# Button > to Ctrl Z (undo)
xsetwacom set pad Button3 "core key ctrl y"
# Button FN2 to Ctrl Y (redo)
xsetwacom set pad Button4 "core key ctrl z"

#setting the buttons on the stylus
# xsetwacom set stylus Button3 3
```

Were you able to use the tablet after plugging it and without restarting X? I have to do it each time I unplug...

---

### Post by srilyk on 2008-11-30
I've been able to get it working by simply suspending and then resuming... which means I don't have to completely restart my lappy, but I'm sure there's some process there that I *should* be able to do with my laptop on.

However, I don't know what that is yet.

---

### Post by sethtriggs on 2009-03-25
I'm getting this issue too.

```

Mar 25 23:01:01 hamilton kernel: [ 1451.488391] usb 2-4: new low speed USB device using ohci_hcd and address 28
Mar 25 23:01:02 hamilton kernel: [ 1451.700334] usb 2-4: configuration #1 chosen from 1 choice
Mar 25 23:01:02 hamilton kernel: [ 1451.707996] input: Wacom Graphire3 6x8 as /devices/pci0000:00/0000:00:02.1/usb2/2-4/2-4:1.0/input/input13
Mar 25 23:01:02 hamilton logger: device input13 is bound to the driver
Mar 25 23:01:02 hamilton logger: must rebind

```

I'd like to see if someone else is getting the same problem.

-Seth

---

### Post by Favux on 2009-03-25
Hi sethtriggs,

You could try the old hotplug commands.  I think they are ctrl-alt-F1 followed by ctrl-alt-F7.

---

### Post by sethtriggs on 2009-03-27
> **Favux said:**
> Hi sethtriggs,

You could try the old hotplug commands.  I think they are ctrl-alt-F1 followed by ctrl-alt-F7.

OK I'll give those a try. I am now in a situation where the tablet will just stop working (I am leaving my computer on) after a while and I have to remove it and then reinsert it, plus restart X with Ctrl-Alt-Backspace to make it function again.

I dropped the tablet once so the light doesn't come on.

And interestingly the device is always present in lsusb. This just started happening a couple days ago.

Does anyone know if any recent updates to Ubuntu would've done something that would break the /dev/input/wacom link that would require you to restart X?

-Seth

---

### Post by sethtriggs on 2009-03-28
> **Favux said:**
> Hi sethtriggs,

You could try the old hotplug commands.  I think they are ctrl-alt-F1 followed by ctrl-alt-F7.

These unfortunately did not work for me - they just switched the modes but did not help with hotplugging. And I have no idea what's killing the /dev/input/wacom .

-Seth

---

### Post by Favux on 2009-03-28
Hi sethtriggs,

That's too bad.  It works for me if Wacom doesn't kick in after a suspend, and for most other tablet pc's, at least of my type, that I know about.

The /dev/input/wacom doesn't work that way.  That's a symlink to the underlying by-path pci usb input.  If the blah-blah-wacom.rules file is present in rules.d then you have the symlink.  So the question is is something affecting usb input?

I don't know if lsusb is dynamic.  Does it reflect hotplug changes?  So maybe it would be better to query the kernel buffer before and after a "glitch".
```
dmesg | grep [Ww]acom
```
If the Wacom kernel driver (module) isn't present after a glitch that may be the problem.  What version of linuxwacom drivers and tools do you have?  I know the latest development branch driver 0.8.3-1 has another hotplug patch.  So this seems to be an ongoing issue.

That said has something changed with your usb setup?  Did you add a new device?  A new hub?  Any damage to the usb cable?

---

### Post by ntpif on 2009-08-29
I also have simillar problem with my Wacom Volito2.
I managed to resolve it by reloading wacom kernel module:
Under the root execute:
```

rmmod wacom;modprobe wacom
```
If you have several graphical sessions active, it may be needed to switch between them ( Ctrl+Alt+F8  <-> Ctrl+Alt+F7)

[]("http://risujin.org/debian/portege_m200.jpg")

---


---
title: "HP Pavilion dv6500 **series** resume issues (8.04)"
date: 2008-06-12
forum: Hardware
---

### Post by pedrogfrancisco on 2008-06-12
Hi!

If you have a HP Pavilion dv6500 **series** read on.
If not but if you can contribute with anything else that isn't *pure* guessing (like "Hey, try nolapic! noapic! noacpi! nosmp!"), read on.
If not, read on as well :P

My "HP Pavilion dv6500 Notebook PC" (which is actually a "HP Pavilion dv6640ep Notebook PC") doesn't always resume successfully.

It was supposed to. It has been marked in /usr/share/hal/fdi/information/10freedesktop/20-video-quirk-pm-hp.fdi
```

        <match key="system.hardware.product" contains_outof="dv2000;dv2500;tx100
0;dv5000 (EZ535UA#;HP Pavilion dv6500 Notebook PC ">
          <merge key="power_management.quirk.none" type="bool">true</merge>
        </match>
      </match>

```
As not having any quirks.

Ah:
```
$ hal-device  |grep "system.hardware.product"
  system.hardware.product = 'HP Pavilion dv6500 Notebook PC'  (string)

```

So, what am I missing here?


IMPORTANT NOTES TO CONSIDER:
NOTE1: the laptop seems to always successfully resumes after a suspend if nothing in its "environment" has changed: AC, connected peripherals, all in the same condition; the moment I start to change its "environment" conditions it stops resuming;
NOTE2: I have used resume successfully in the past with Gutsy Gibbon (7.10) and after an upgrade to 8.04; later I made a clean install of Kubuntu and started noticing these resume failures;
NOTE3: I also face issues when restoring the state from hibernation. Sometimes it fails; sometimes it fails to switch to X; if I switch to X manually the machine seems to crash and not even the "Magic Keys" (Alt+SysRq+KEY) work.


[B]So, to everyone using this laptop out there, does your work with no fancy stuff?
[/B]



lspci:
```
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

---

### Post by pedrogfrancisco on 2008-06-13
I initiated a forced shutdown in order to debug the issue, as described [here]("https://wiki.ubuntu.com/DebuggingKernelSuspend") and got this:

```

[   14.020567]   Magic number: 0:968:286
[   14.020619]   hash matches /build/buildd/linux-2.6.24/drivers/base/power/main.c:112
[   14.020693]   hash matches device ttyz0

```

So /dev/ttyz0 is to blame? (??!!).

P.S.: ocurred to me now after writing all this it'd be smart of me to suspend from the command line, with no X running. Will do it now.

---

### Post by ravl on 2008-06-13
I installed Kubunty 8.04 on a HP Pavillion dv6810 and everything worked right out of the box. Quickplay buttons, IR remote control.
I do have an issue after suspending, my wireless card stops working. I have to manually remove and reload ndiswrapper after resuming. Don't think it's really related to hardware though.

---

### Post by pedrogfrancisco on 2008-06-13
Thanks for your input ravl!

AFAIK, the IR works everywhere, even in the BIOS setup screens ^^

I guess it emulates keystrokes.

Anyway, here are my results:

**Every of the following runs were done without X running:**
```

sudo sh /etc/acpi/sleep.sh

```
FAIL. Horribly. It doesn't even suspend, hangs, *while suspending* in the same condition as if it had been resuming from a "normal" suspend initiated by a KDE session: black screen and not even the enable/disable touchpad button works (for some stupid reason I always forget testing CAPS LOCK but always remember the enable/disable touchpad button)


```

sudo sh /etc/acpi/hibernate.sh

```
FAIL. Even more horribly. Gets me one of those screens which remind me of a kernel panic, with a lot of hex stuff, traces, callbacks, whatever (didn't get the values, too lazy) and then hangs.

Now for the "even more horribly": shutting down and powering up the computer initiates a "de-hibernation" procedure which hangs at the time a console should be displayed. Stupidly, ALT-ARROW and CTRL-ALT-Function keys work, effectively showing me tty2 and thus, a console, but none of the other keys work. Didn't try Magic Keys.


```

sudo -s
echo 1 > /sys/power/pm_trace
pmi action suspend

```
FAIL. This time I get in dmesg:

```

[   14.219830]   Magic number: 0:731:44
[   14.219880]   hash matches /build/buildd/linux-2.6.24/drivers/base/power/main.c:76
[   14.219947]   hash matches device ttyed

```
ttyed... A while ago was ttyz0 and now ttyed... Maybe a rm /dev/tty* will solve my problem? *drools* (**newbie alert: this is, in case you're a newbie not aware of /dev role, a *big* joke, rm /dev/tty* wouldn't do any good ;)**)


Bah what the hell... Unless someone has a "I got it" moment I'm gonna put this on hold and try the fancy stuff [here]("http://ubuntuforums.org/showthread.php?t=505890") later in July.

---

### Post by pedrogfrancisco on 2008-06-14
Ok guys, here are some news: compiled 2.6.26-rc6 (git pulled yesterday) with the procedure detailed [here]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild") and my computer now succesfully suspend and resumes from within KDE. As such haven't tried other methods and consider this issue kinda fixed :)

Anyway I'm filling in a bug report on this, I'll post the link here later.

---

### Post by pedrogfrancisco on 2008-06-14
Ok, this is stupid: I rebooted to the old kernel (the stock kernel, 2.6.24-18-generic) just to check one last time suspend was broken and suspend worked...

:confused:](*,):evil:

How annoying can that be?

No bug report has been filled nor will be until/if I get the suspend issue again.

---

### Post by jarviw on 2009-07-20
So do you still have the problem? Are you still using Hardy?
I have the same problem as well in my dv6500, and I remember hibernation worked in Gutsy, but never worked since. (all right, maybe it finally worked in Hardy, but now I am running Jaunty.)

I think it may be a problem in the BIOS.
It hibernates in Vista, but I am yet to have it to wake up in XP.

Have you found the source of the problem?

---

### Post by pedrogfrancisco on 2009-08-31
Weird don't remember being notified of your participation here by mail.

The problem appeared and disappeared by itself, never got to find out which the problem was.

I've used 8.10 and 9.04 and suspend works.

EDIT: and on XP also works.

---


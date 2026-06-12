---
title: "cd drive not working"
date: 2011-04-28
forum: Hardware
---

### Post by Tadcrazio on 2011-04-28
So my laptop running 10.10 fails to recongize my cd/dvd drive. When I put a disk in the drive revs up and spins but fails to acknowledge there is a disk in the drive. It started last week and i threw in a live cd and it loaded it from start and then it started working. However today i wanted to install 11.04 i downloaded the iso and with my luck the drive fails to work. So i downloaded the iso on another computer rebooted my laptop with the cd in and it went right to my ubuntu desktop. So now i can even get it to load a live cd. Any suggestions on what to do?

---

### Post by Tadcrazio on 2011-04-29
Well I burned a 11.04 and it started to install, then it stopped and said there was an input output error. I tried numerous disks all burned at different write speeds, none worked correctly. So I trIed other disks I had laying around with no luck. So I figured my disk drive was bad. Got readybto take to worst buy because it's under warranty so I threw in my restore disks for kicks and they work!!! Why won't ubuntu work!?

---

### Post by linuxyogi on 2011-04-29
Why didn't you try to install using a USB drive ? 


Its all explained here  [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

I once used this tool [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) to create a bootable usb drive from a Ubuntu iso image.

After you prepare the usb drive you need to configure the bios in order to boot from usb.

---

### Post by Tadcrazio on 2011-04-29
I failedto mention that I did, several times I keep getting a boot error

---

### Post by linuxyogi on 2011-04-29
> **Tadcrazio said:**
> I failedto mention that I did, several times I keep getting a boot error

plug in the usb disk

boot the laptop 

now look carefully at the screen 

look for the line Press F[no] to select boot device.

If the laptop displays a fullscreen splash screen that needs to be disable via bios to be able to see this screen. 

Then boot & press F (whatever) then select boot device from there

if usb fails

select hard drive and see if your usb drive has been recognized as a second hard drive

select that & boot

---

### Post by Tadcrazio on 2011-04-29
> **linuxyogi said:**
> plug in the usb disk

boot the laptop 

now look carefully at the screen 

look for the line Press F[no] to select boot device.

If the laptop displays a fullscreen splash screen that needs to be disable via bios to be able to see this screen. 

Then boot & press F (whatever) then select boot device from there

if usb fails

select hard drive and see if your usb drive has been recognized as a second hard drive

select that & boot

I have no idea what you are saying. I have set my bios up to start from USB and selected it. It never works correctly tho

---

### Post by linuxyogi on 2011-04-29
> **Tadcrazio said:**
> I have no idea what you are saying. I have set my bios up to start from USB and selected it. It never works correctly tho

Most bios lets you select the boot device using a selection window which appears after pressing a particular function key.

 In my case its F9. If I press F9 at the beginning of the boot process (like you do to enter your bios) a screen appears which allows me to select the device from which I want to boot the PC.

You need to figure out which function key does the same in your bios.

Just try F9 & see if that works. Keep pressing F9 at the beginning of the boot process just like you press del (or F2) to enter setup.

---

### Post by Tadcrazio on 2011-04-29
> **linuxyogi said:**
> Most bios lets you select the boot device using a selection window which appears after pressing a particular function key.

 In my case its F9. If I press F9 at the beginning of the boot process (like you do to enter your bios) a screen appears which allows me to select the device from which I want to boot the PC.

You need to figure out which function key does the same in your bios.

Just try F9 & see if that works. Keep pressing F9 at the beginning of the boot process just like you press del (or F2) to enter setup.

Yea that's what I was trying to say I already did. Sometimes I get a splash screen but it never works correctly. I'm rather perplexed on why my cd drive isn't working tho

---

### Post by Tadcrazio on 2011-04-30
Well the drives kaput, now to explain to geek squad why I have no os on it..

---


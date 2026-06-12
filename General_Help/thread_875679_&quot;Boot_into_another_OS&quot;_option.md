---
title: "&quot;Boot into another OS&quot; option"
date: 2008-07-31
forum: General Help
---

### Post by Grape_Soda on 2008-07-31
Hi, I just upgraded my computer and decided to give Ubuntu a try.  I've used SUSE since 9.3 and might be installing 11.0 if I can't get this figured out.  

I have a keyboard that doesn't work until the OS is loaded.  So I can't use the boot loader to choose what I want to boot into.  SUSE has the option to boot into another OS when you restart.  Is there anything like that in Ubuntu?

---

### Post by iaculallad on 2008-07-31
> **Grape_Soda said:**
> Hi, I just upgraded my computer and decided to give Ubuntu a try.  I've used SUSE since 9.3 and might be installing 11.0 if I can't get this figured out.  

I have a keyboard that doesn't work until the OS is loaded.  So I can't use the boot loader to choose what I want to boot into.  SUSE has the option to boot into another OS when you restart.  Is there anything like that in Ubuntu?

Yes there is, and you can edit it through /boot/grub/menu.lst to change the booting order of the OS installed/configured.

---

### Post by Grape_Soda on 2008-07-31
I forgot to add that I dual boot Vista and linux.  Since my keyboard doesn't work in grub, I need some way to get into Vista when I need to.

I used to have grub boot to SUSE by default and to get to windows, I would choose the "Boot into Windows" while in SUSE.

---

### Post by iaculallad on 2008-07-31
> **Grape_Soda said:**
> I used to have grub boot to SUSE by default and to get to windows, I would choose the "Boot into Windows" while in SUSE.

Same process applies to Ubuntu, you can choose the "windoze" OS (selecting it on menu) you whenever you like because by default, Ubuntu is configured to boot first. You're keyboard should have been already initialized at this stage.

---

### Post by Grape_Soda on 2008-07-31
You're talking about in grub correct?  My keyboard isn't initialized at that point.  What I am talking about is going to the suse button>leave>restart into another OS>Windows Vista.

My keyboard is the Razor Tarantula and is known to not work until the OS loads.  There has been a update for it that lets it work in the BIOS but it doesn't work after that.

---

### Post by dexter.deepak on 2008-07-31
you can even use the windows bootloader to boot linux.
[http://www.linux.com/feature/113945](http://www.linux.com/feature/113945)

anyways, you can also change the entry called :
```
default 0
```
to make the default OS to be loaded (n) as :
```
default (n-1)
```

---

### Post by iaculallad on 2008-07-31
I think there is a compatibility issue with GRUB so that option of putting "Boot to windoze" on reboot to the (shutdown/logoff/lock screen menu) is ignored. And by the way, why should Ubuntu care on putting that option anyway.

---

### Post by zvacet on 2008-07-31
@ **Grape_Soda**

You can use Ubuntu alternate Cd to install and you will not need keyboard for that.Add Ubuntu entries to Suse grub and you will be able to boot in desired OS.

---

### Post by adewale on 2008-07-31
I use a usb keyboard which doesn't work until when the os loads. The solution was in cmos and something like enabled usb legacy device and thumb support for dos.

---

### Post by zvacet on 2008-07-31
@ **Grape_Soda**

Just forget what I suggested to you.

---


---
title: "Laptop hangs on shutdown"
date: 2008-09-02
forum: General Help
---

### Post by liquidcross on 2008-09-02
I'm running a Thinkpad R60 with 8.04. Every time I shut down, the system hangs on "Running local boot scripts (/etc/rc.local)..." The only way to continue the shutdown is to wait a few minutes, then press the power button. After that, it shuts down as normal.

Any fixes?

---

### Post by monkeyking on 2008-09-02
I remember having similar problem on slackware years ago.
You should check what makes the program crash.

When you tell it to shutdown hit,

ctrl+alt f1 or something, this will get you to the terminal that tells what happens.

Also try starting in recovery mode,
and the restart. sudo init 6.

And check what happens.

good luck

---

### Post by liquidcross on 2008-09-03
Okay, I tried that, and I had to take a photo of the screen (the messages were scrolling to fast!). The image is attached. Any thoughts?

---

### Post by monkeyking on 2008-09-03
Are these the last lines before, it crashes?

If so, I would simply uninstall network manager.

Setting up the network afterwards should be quite simple.
something like 
```
ifup eth0
```

You should also set up /etc/network/interfaces file, if you decide to drop network-manager.

```

auto eth0
iface eth0 inet dhcp

```


network manager is simply a easy front end for setting up your network, so you should be able to manage.

---

### Post by porchrat on 2008-09-03
I've seen this problem often...it's been around for a while.

Does it ever stop with 'linux halted' at the end?

hal and dbus ned network manager to shutdown properly, I have a similar error at the end of my shutdown and mine shutdowns fine.

If it merely stops without turning off it could be acpi

---

### Post by monkeyking on 2008-09-03
You can also try setting reboot=b in your /boot/grub/menu.lst

---

### Post by porchrat on 2008-09-03
> **monkeyking said:**
> You can also try setting reboot=b in your /boot/grub/menu.lst

ooooh what does that do?

(I tried googling but it is late and I am just feeling too lazy to research things right now)

---

### Post by monkeyking on 2008-09-03
I'm not really sure, I haven't been able to find reliable info about this.

But it seems you can tell linux how the system should do a reboot/boot.

reboot=b is bios, reboot=c is a cold boot, There are many other options I think.

But I solved my shutdown problem with reboot=b

good luck

---

### Post by liquidcross on 2008-09-09
Right now, my laptop connects to my home wifi network in roaming mode. If I get rid of NetworkManager, will that make it more difficult to connect?

I'm also going to try the reboot=b trick when I get home. I assume I can place that anywhere within /boot/grub/menu.lst?

---

### Post by monkeyking on 2008-09-09
You don't need to edit the menu.lst, to set reboot=b.

Press escape when ubuntu boots, this will bring you to the boot menu,
choose the top one, this should be your default.
But don't press enter, press e, for edit I think.

Then put reboot=b as the last item on the line.

That should do it.

---


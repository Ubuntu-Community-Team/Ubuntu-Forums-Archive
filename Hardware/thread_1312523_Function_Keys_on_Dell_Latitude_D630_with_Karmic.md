---
title: "Function Keys on Dell Latitude D630 with Karmic"
date: 2009-11-03
forum: Hardware
---

### Post by tincup on 2009-11-03
Hi.

I freshly installed Karmic (Kubuntu) on a Dell Latitude D630. Everything works pretty fine out of the box, except for some function keys.

For instance, Fn-F1 = Hibernate and Fn-F8 = toggle CRT/LCD do not work.

If I watch the keyboard events however, there seems to be at least some signal:

```

$ lshal -m

Start monitoring devicelist:
-------------------------------------------------
12:44:51.445: platform_i8042_i8042_KBD_port_logicaldev_input condition ButtonPressed = hibernate
12:44:52.806: platform_i8042_i8042_KBD_port_logicaldev_input condition ButtonPressed = switch-videomode

```

... but nothing happens. Any ideas? Can I configure the executed scripts for "hibernate" and "switch-videomode" manually?

Thanks in advance,
 tin

---

### Post by penguin-power on 2009-11-03
> **tincup said:**
> Hi.

I freshly installed Karmic (Kubuntu) on a Dell Latitude D630. Everything works pretty fine out of the box, except for some function keys.

For instance, Fn-F1 = Hibernate and Fn-F8 = toggle CRT/LCD do not work.

If I watch the keyboard events however, there seems to be at least some signal:

```

$ lshal -m

Start monitoring devicelist:
-------------------------------------------------
12:44:51.445: platform_i8042_i8042_KBD_port_logicaldev_input condition ButtonPressed = hibernate
12:44:52.806: platform_i8042_i8042_KBD_port_logicaldev_input condition ButtonPressed = switch-videomode

```... but nothing happens. Any ideas? Can I configure the executed scripts for "hibernate" and "switch-videomode" manually?

Thanks in advance,
 tin


y not just download the official dell in stall dvd? this dvd makes everything work as dell would ship it. 

link:
[http://linux.dell.com/files/ubuntu/karmic/iso-images/ubuntu-9.10-dell_X02.iso](http://linux.dell.com/files/ubuntu/karmic/iso-images/ubuntu-9.10-dell_X02.iso)

( the above is the very latest dell-ubuntu release.)

also, dell wiki here:
[http://en.community.dell.com/wikis/linux/ubuntu-9-10.aspx](http://en.community.dell.com/wikis/linux/ubuntu-9-10.aspx)


hope it helps!

will

---

### Post by recluce on 2009-11-06
> **penguin-power said:**
> y not just download the official dell in stall dvd? this dvd makes everything work as dell would ship it. 

link:
[http://linux.dell.com/files/ubuntu/karmic/iso-images/ubuntu-9.10-dell_X02.iso](http://linux.dell.com/files/ubuntu/karmic/iso-images/ubuntu-9.10-dell_X02.iso)

( the above is the very latest dell-ubuntu release.)

also, dell wiki here:
[http://en.community.dell.com/wikis/linux/ubuntu-9-10.aspx](http://en.community.dell.com/wikis/linux/ubuntu-9-10.aspx)


hope it helps!

will

It will not help if you run / want to run the 64bit version, Dell install is 32 bit only. Other than that, probably good advice on problematic Dells.

Has anybody else had that issue? Would be a death-blow for Karmic on my machine, as I need the "Fn" "F8" combo to activate my external screen when the laptop is docked. I cannot see my internal display in this case, as the dock has the Dell monitor stand.

To the OP: does "Scroll-Lock" and "F8" on an external keyboard work?

---


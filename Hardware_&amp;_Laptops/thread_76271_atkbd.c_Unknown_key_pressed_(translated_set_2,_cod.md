---
title: "atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0)"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by yabaman on 2005-10-14
I'm using Ubuntu Breezy Badger, and most recently updated.

after the last update, dmesg shows messages like follows.

```
[4295109.888000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295109.888000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295109.994000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295109.994000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295110.083000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295110.083000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295110.199000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295110.199000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295110.292000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295110.292000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295110.403000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295110.403000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
```

I'm using ubuntu on HP pavilion zt3337 AP.

How can I solve this problem?

related thread - 
[http://www.ubuntuforums.org/showthread.php?t=74504&highlight=atkbd.c](http://www.ubuntuforums.org/showthread.php?t=74504&highlight=atkbd.c)

---

### Post by gbusse on 2005-10-15
Same problem here, generic PC. Would also like to know what is up with this?

---

### Post by Arno_A on 2005-10-16
The same problem here. I started noticing these entries:

[FONT="Courier New"]Oct 16 13:32:47 localhost kernel: [4309914.879000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Oct 16 13:32:47 localhost kernel: [4309914.879000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Oct 16 13:32:48 localhost kernel: [4309915.634000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
Oct 16 13:32:48 localhost kernel: [4309915.634000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Oct 16 13:32:48 localhost kernel: [4309915.806000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Oct 16 13:32:48 localhost kernel: [4309915.806000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Oct 16 13:32:49 localhost kernel: [4309916.543000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
Oct 16 13:32:49 localhost kernel: [4309916.543000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Oct 16 13:32:49 localhost kernel: [4309916.680000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Oct 16 13:32:49 localhost kernel: [4309916.680000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[/FONT]

I have an x86 machine with a Finnish PS2 PS/2 105 key keyboard.

Initially I suspected that this behaviour started after using the Automatix script, to map CTRL-Alt-Delete to the Gnome system monitor.

Arno

---

### Post by Bolorino on 2005-10-16
Same here.

First I look in System/Preferences/Keyboard (I think. I use spanish)

My keboard (spanish) has 21 specials keys (music player, web browsing, and so on). In the settings these keys were assigned (first time I see that) so I played for a while reconfiguring the settings. Works OK.

Then I took a look to /var/log/messages with:

```
tail -f /var/log/messages
```

to see what happens while pressing some keys.

I get the error messages:

```
Oct 16 13:43:49 localhost kernel: [4307418.520000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Oct 16 13:43:49 localhost kernel: [4307418.520000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

```

when pressing the arrows keys!

And I don't know more.

Sorry if my english is not good enough

---

### Post by ghostdog on 2005-10-16
I have the same issue, I upgraded from hoary to breezy. Then I reinstalled breezy and also tried on a second machine.

I own a US keyboard.

---

### Post by snowflake on 2005-10-18
Hi, 

I had the same problem. I found a script, called hotkey-setup in init.d, which is started every boot. I stopped this program and now it's working properly, there isn't any  errors in logs.

---

### Post by dammit_jim on 2005-10-20
Apparently hotkey-setup is used to automatically bind special laptop keys. I got the same error and fixed it using rcconf and unchecking hotkey-setup.

To stop the process from running without rebooting you can use

```
sudo /etc/init.d/hotkey-setup stop
```

If that fixes it, then try stopping hotkey-setup permanently.

```

sudo apt-get install rcconf
sudo update-rcconf-guide
sudo rcconf

```

Then uncheck the hotkey-setup service.

Hope that helps!

---

### Post by CarNagE on 2005-10-22
Found no other possibility to delete my statement, which was erroneous.

---

### Post by Xk2c on 2005-10-22
There is request in bugzilla for this case also:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=17569](https://bugzilla.ubuntu.com/show_bug.cgi?id=17569)

PS. and I did also sudo update-rc.d -f hotkey-setup remove yesterday.
      but today I got those messages again.

---

### Post by krisek on 2005-10-24
have a look on this site:

[http://wiki.ubuntu-fr.org/materiel/clavier_multimedia](http://wiki.ubuntu-fr.org/materiel/clavier_multimedia)

or:

sudo vi /etc/init.d/bootmisc.sh

and put somewhere before :exit 0 this

setkeycodes e025 129

where e025 is the keycode that cannot be resolved

---

### Post by Xk2c on 2005-10-24
[QUOTE=krisek]and put somewhere before :exit 0 this

setkeycodes e025 129

where e025 is the keycode that cannot be resolved[/QUOTE]

I don&#180;t want to be a killjoy, but what about:

Oct 24 19:07:17 localhost kernel: [4299114.472000] atkbd.c: Unknown key pressed (translated set 2, code 0x92 on isa0060/serio0).
Oct 24 19:07:17 localhost kernel: [4299114.472000] atkbd.c: Use 'setkeycodes e012 <keycode>' to make it known.
Oct 24 19:07:17 localhost kernel: [4299114.587000] atkbd.c: Unknown key pressed (translated set 2, code 0x98 on isa0060/serio0).
Oct 24 19:07:17 localhost kernel: [4299114.587000] atkbd.c: Use 'setkeycodes e018 <keycode>' to make it known.
Oct 24 20:17:26 localhost kernel: [4303326.991000] atkbd.c: Unknown key pressed (translated set 2, code 0x8a on isa0060/serio0).
Oct 24 20:17:26 localhost kernel: [4303326.991000] atkbd.c: Use 'setkeycodes e00a <keycode>' to make it known.


? ? ?

which one should I choose?

PS. I did "sudo update-rc.d -f hotkey-setup remove"  the day before yesterday

---

### Post by seldon77 on 2005-11-11
try:

sudo chmod -x /etc/init.d/hotkey-setup

---

### Post by jliedeka on 2005-11-11
Why not:
sudo su
cd /etc/init.d
rm hotkey-setup
ln -s /bin/true hotkey-setup

:-p

---

### Post by jliedeka on 2005-11-11
Seriously, all hotkey-setup does is source a file from /usr/share/hotkey-setup, except for Sonys.  For sony it loads the sonypi module.  That's what mine does and I see the errors as well.

     Jim

---

### Post by ranf on 2005-11-12
[QUOTE=jliedeka]Seriously, all hotkey-setup does is source a file from /usr/share/hotkey-setup, except for Sonys.  For sony it loads the sonypi module.  [/QUOTE]
It always runs:
```
. /usr/share/hotkey-setup/generic.hk
```

---

### Post by jliedeka on 2005-11-15
I actually think, in my case, that symptom had nothing to do with my keyboard.  It went away after I got my wireless and sound working.  It seems damn near everything uses IRQ 9 so it's possible it was coming from somewhere else.  Plus I ran  xev  and couldn't find any key, mouse click or key combo that had the code e02a.

---

### Post by chung on 2005-12-28
I've the same error messages.
Disabling hotkey-setup cannot solve my problem. I discover that the problem is caused by the discrepance between the xwindow and the gnome keyboard settings: I changed the keyboard setting in gnome without caring about the xorg.conf file. After adjusting the InputDevice entries in xorg.conf, the error messages disappear.

location of xorg.conf: /etc/X11
explanation of syntax: [http://www.xfree86.org/current/XKB-Config.pdf](http://www.xfree86.org/current/XKB-Config.pdf)
explanation of smybols: /etc/X11/xkb/rules/base base.lst

Good luck!

---

### Post by ploom on 2006-01-03
[QUOTE=jliedeka]I actually think, in my case, that symptom had nothing to do with my keyboard.  It went away after I got my wireless and sound working.  It seems damn near everything uses IRQ 9 so it's possible it was coming from somewhere else.  Plus I ran  xev  and couldn't find any key, mouse click or key combo that had the code e02a.[/QUOTE]


Believe you should try shift + PgUp or shift + PgDown keys to scroll terminal lines up/down. At least on my ubuntu pc both key-pressings result in something following (in addition to scrolling the text as expected):

```

[4297601.557000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297601.557000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297601.623000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297601.623000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

```

Please note that "key released" line really comes before "key pressed" one...

---

### Post by amarra on 2006-01-04
I've had the same problem on two different PCs, a desktop one (with ASUS K8V Deluxe mainboard) and a laptop one (an ASUS W3N).
In both of them I found the system log filled with the error "... Unknown key released..." as you reported before.
I've searched around to find a way to fire up the suggested "setkeycodes e02a <keycode>" command by inserting it in various init.d scripts, and even to create a new one, but none of them functioned.
When I read from you about the "hotkey-setup" script, I've seen that the [FONT=monospace]/[/FONT]usr/share/hotkey-setup/generic.hk file contains, between the others, the following line:

setkeycodes e02a 256

I've changed it to read as:

setkeycodes e02a 120

given that the keycode 120 is generally not assigned to any scancode.
This solved my troubles in both the desktop and the laptop PCs.
I hope this can help you.

Bye.

---

### Post by Titan1958 on 2006-01-09
Solve the proble for me!Thanks :)

---

### Post by ghostdog on 2006-01-10
[QUOTE=dammit_jim]Apparently hotkey-setup is used to automatically bind special laptop keys. I got the same error and fixed it using rcconf and unchecking hotkey-setup.

To stop the process from running without rebooting you can use

```
sudo /etc/init.d/hotkey-setup stop
```

If that fixes it, then try stopping hotkey-setup permanently.

```

sudo apt-get install rcconf
sudo update-rcconf-guide
sudo rcconf

```

Then uncheck the hotkey-setup service.

Hope that helps![/QUOTE]

That did the trick, thanks.

---

### Post by dcstar on 2006-01-19
Or:

[http://ubuntuforums.org/showthread.php?p=669419&posted=1#post669419](http://ubuntuforums.org/showthread.php?p=669419&posted=1#post669419)

---

### Post by jayseye on 2007-12-20
Has anyone tested this fix under Ubuntu 7.10 Gutsy Gibbon? Some other proposed solutions, for Dell Inspiron 1501, have been reported to cause more damage than they solve. So would like confirmation for Gutsy before testing this one: 

> **dammit_jim said:**
> Apparently hotkey-setup is used to automatically bind special laptop keys. I got the same error and fixed it using rcconf and unchecking hotkey-setup.

To stop the process from running without rebooting you can use

```
sudo /etc/init.d/hotkey-setup stop
```

If that fixes it, then try stopping hotkey-setup permanently.

```

sudo apt-get install rcconf
sudo update-rcconf-guide
sudo rcconf

```

Then uncheck the hotkey-setup service.

Hope that helps!

---

### Post by wonton180 on 2008-02-08
> **jayseye said:**
> Has anyone tested this fix under Ubuntu 7.10 Gutsy Gibbon? Some other proposed solutions, for Dell Inspiron 1501, have been reported to cause more damage than they solve. So would like confirmation for Gutsy before testing this one:

I too have an Dell Inspiron 1501 with AMD Sempron.  The scancode -> keycode mapping does work using "setkeycode xxx xxx".  but i think it's just merely suppressing kernel logging.  the atkbd keyboard driver is still parsing what looks like keypresses.  On my machine this happens very frequently...note the timestamps:

[ 2446.844000] atkbd.c: Unknown key released (translated set 2, code 0x8d on isa0060/serio0).
[ 2446.844000] atkbd.c: Use 'setkeycodes e00d <keycode>' to make it known.
[ 2448.876000] atkbd.c: Unknown key pressed (translated set 2, code 0x8d on isa0060/serio0).
[ 2448.876000] atkbd.c: Use 'setkeycodes e00d <keycode>' to make it known.
[ 2448.888000] atkbd.c: Unknown key released (translated set 2, code 0x8d on isa0060/serio0).
[ 2448.888000] atkbd.c: Use 'setkeycodes e00d <keycode>' to make it known.
[ 2449.908000] atkbd.c: Unknown key pressed (translated set 2, code 0x8d on isa0060/serio0).
[ 2449.908000] atkbd.c: Use 'setkeycodes e00d <keycode>' to make it known.
[ 2449.920000] atkbd.c: Unknown key released (translated set 2, code 0x8d on isa0060/serio0).
[ 2449.920000] atkbd.c: Use 'setkeycodes e00d <keycode>' to make it known.

i guess these keyboards are doing some kind of heartbeat ?  there should be a way to map these scan codes to idle/noop actions.

---

### Post by riskbreaker927 on 2008-04-20
I have this same issue on my Dell Inspiron 1501.

For what it's worth, I dont think this is a Linux issue. In Windows Vista (I dualboot) some times i'll be in a program, for example an emulator that lets me define a key as a control in a game, and I'm unable to set these keys unless i do it within a small timeframe because it automatically sets a nondescript key. Also, in windows, I'm unable to see tooltips for more than a split second, because this phantom key is being pressed.

I'll be on the phone with Dell support today.

---

### Post by duruttye on 2008-05-07
Hey!

Any news on this issue?

Having a 32bit 7.10 ubuntu on a 64bit dell inspiron 1501, never had this problem with 64bit edition...

It's filling up the logs.

---

### Post by Skretch on 2008-07-08
Try this solution: [http://ph.ubuntuforums.com/showthread.php?p=5342606#post5342606](http://ph.ubuntuforums.com/showthread.php?p=5342606#post5342606)

---


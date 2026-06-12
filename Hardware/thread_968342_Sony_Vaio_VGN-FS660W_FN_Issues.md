---
title: "Sony Vaio VGN-FS660W FN Issues"
date: 2008-11-02
forum: Hardware
---

### Post by brianjcollins on 2008-11-02
I've searched, read, and just about cried.  For the life of me, I cannot get this sony vaio's function keys to work.

I'm using ubuntu 8.10..

Linux brian-laptop 2.6.27-7-generic #1 SMP Thu Oct 30 04:18:38 UTC 2008 i686 GNU/Linux

*lsmod |grep sony
sony_laptop            39004  0 

I don't get a key response from xev, the only thing I can see really is in the message log.

--
[ 1653.108862] atkbd.c: Use 'setkeycodes e075 <keycode>' to make it known.
[ 1653.180864] atkbd.c: Unknown key released (translated set 2, code 0xf5 on isa0060/serio0).
[ 1653.180878] atkbd.c: Use 'setkeycodes e075 <keycode>' to make it known.
[ 1653.315685] atkbd.c: Unknown key pressed (translated set 2, code 0xf5 on isa0060/serio0).
[ 1653.315699] atkbd.c: Use 'setkeycodes e075 <keycode>' to make it known.
[ 1653.401443] atkbd.c: Unknown key released (translated set 2, code 0xf5 on isa0060/serio0).
--

Over and over each time I hit one of the function keys.  I've followed several faqs, even outdated ones, nothing has seemed to change the outcome.  I hope im just missing something.

Thanks,
Brian

---

### Post by brianjcollins on 2008-11-02
When I try to listen to the ACPI daemon for keystrokes, it returns nothing for the function keys.  All other keys work, but no functions.  All the scripts work within /etc/acpi/events for volume up/down etc.  I just can't figure out how to make the keys listen and work.

Brian

---

### Post by brianjcollins on 2008-11-02
Apparently it might be the 2.6.27 kernel. I'll try to roll it back and see what happends.

Brian

---

### Post by gianluca.colucci on 2008-11-03
Hi Brian,

have you tried to roll back? if yes, with what results?
I have a VGN-FS515B and I have exactly the same issue.

Thanks,
Gian.

---

### Post by pihhan on 2008-11-04
In fact i think you are quite lucky. You have got direct support for special keys without any daemon or module. What you need to do is to try all fnkeys and get messages from /var/log/kern.log to some file. Maybe compress it and post your /var/log/kern.log here. What you have to do is the command they wrote to you.

```

sudo setkeycodes e075 235

```

This should assign fn-key you pressed symbol 235, which should be then visible in xev command. Try to describe all codes your fnkeys reports to /var/log/kern.log with description, which fn key is that. We may then help you wery quickly. Your problem is that hotkey-setup package does not support your model, it might be very easy to fix.

---

### Post by brianjcollins on 2008-11-05
> **pihhan said:**
> In fact i think you are quite lucky. You have got direct support for special keys without any daemon or module. What you need to do is to try all fnkeys and get messages from /var/log/kern.log to some file. Maybe compress it and post your /var/log/kern.log here. What you have to do is the command they wrote to you.

```

sudo setkeycodes e075 235

```

This should assign fn-key you pressed symbol 235, which should be then visible in xev command. Try to describe all codes your fnkeys reports to /var/log/kern.log with description, which fn key is that. We may then help you wery quickly. Your problem is that hotkey-setup package does not support your model, it might be very easy to fix.

I hit each key and watched the log and as follows.  Notice how each key looks the same, so when I use setkeycodes it binds every key to the symbol.


Nov  5 09:45:50 brian-laptop kernel: [  114.815621] atkbd.c: Unknown key pressed (translated set 2, code 0xf5 on isa0060/serio0).
Nov  5 09:45:50 brian-laptop kernel: [  114.815639] atkbd.c: Use 'setkeycodes e075 <keycode>' to make it known.
Nov  5 09:45:50 brian-laptop kernel: [  114.904284] atkbd.c: Unknown key released (translated set 2, code 0xf5 on isa0060/serio0).
Nov  5 09:45:50 brian-laptop kernel: [  114.904299] atkbd.c: Use 'setkeycodes e075 <keycode>' to make it known.
Nov  5 09:45:52 brian-laptop kernel: [  116.186513] atkbd.c: Unknown key pressed (translated set 2, code 0xf5 on isa0060/serio0).
Nov  5 09:45:52 brian-laptop kernel: [  116.186531] atkbd.c: Use 'setkeycodes e075 <keycode>' to make it known.
Nov  5 09:45:52 brian-laptop kernel: [  116.276084] atkbd.c: Unknown key released (translated set 2, code 0xf5 on isa0060/serio0).
Nov  5 09:45:52 brian-laptop kernel: [  116.276099] atkbd.c: Use 'setkeycodes e075 <keycode>' to make it known.
Nov  5 09:45:53 brian-laptop kernel: [  117.053896] atkbd.c: Unknown key pressed (translated set 2, code 0xf5 on isa0060/serio0).
Nov  5 09:45:53 brian-laptop kernel: [  117.053913] atkbd.c: Use 'setkeycodes e075 <keycode>' to make it known.
Nov  5 09:45:53 brian-laptop kernel: [  117.153024] atkbd.c: Unknown key released (translated set 2, code 0xf5 on isa0060/serio0).
Nov  5 09:45:53 brian-laptop kernel: [  117.153039] atkbd.c: Use 'setkeycodes e075 <keycode>' to make it known.
Nov  5 09:45:53 brian-laptop kernel: [  117.823278] atkbd.c: Unknown key pressed (translated set 2, code 0xf5 on isa0060/serio0).
Nov  5 09:45:53 brian-laptop kernel: [  117.823296] atkbd.c: Use 'setkeycodes e075 <keycode>' to make it known.
Nov  5 09:45:53 brian-laptop kernel: [  117.904373] atkbd.c: Unknown key released (translated set 2, code 0xf5 on isa0060/serio0).
Nov  5 09:45:53 brian-laptop kernel: [  117.904387] atkbd.c: Use 'setkeycodes e075 <keycode>' to make it known.
Nov  5 09:45:54 brian-laptop kernel: [  118.893649] atkbd.c: Unknown key pressed (translated set 2, code 0xf5 on isa0060/serio0).
Nov  5 09:45:54 brian-laptop kernel: [  118.893666] atkbd.c: Use 'setkeycodes e075 <keycode>' to make it known.
Nov  5 09:45:55 brian-laptop kernel: [  118.983732] atkbd.c: Unknown key released (translated set 2, code 0xf5 on isa0060/serio0).
Nov  5 09:45:55 brian-laptop kernel: [  118.983747] atkbd.c: Use 'setkeycodes e075 <keycode>' to make it known.
Nov  5 09:45:55 brian-laptop kernel: [  119.735005] atkbd.c: Unknown key pressed (translated set 2, code 0xf5 on isa0060/serio0).
Nov  5 09:45:55 brian-laptop kernel: [  119.735022] atkbd.c: Use 'setkeycodes e075 <keycode>' to make it known.
Nov  5 09:45:55 brian-laptop kernel: [  119.834139] atkbd.c: Unknown key released (translated set 2, code 0xf5 on isa0060/serio0).
Nov  5 09:45:55 brian-laptop kernel: [  119.834154] atkbd.c: Use 'setkeycodes e075 <keycode>' to make it known.
Nov  5 09:45:56 brian-laptop kernel: [  120.779129] atkbd.c: Unknown key pressed (translated set 2, code 0xf5 on isa0060/serio0).
Nov  5 09:45:56 brian-laptop kernel: [  120.779147] atkbd.c: Use 'setkeycodes e075 <keycode>' to make it known.
Nov  5 09:45:56 brian-laptop kernel: [  120.851197] atkbd.c: Unknown key released (translated set 2, code 0xf5 on isa0060/serio0).
Nov  5 09:45:56 brian-laptop kernel: [  120.851212] atkbd.c: Use 'setkeycodes e075 <keycode>' to make it known.
Nov  5 09:45:57 brian-laptop kernel: [  121.843467] atkbd.c: Unknown key pressed (translated set 2, code 0xf5 on isa0060/serio0).
Nov  5 09:45:57 brian-laptop kernel: [  121.843484] atkbd.c: Use 'setkeycodes e075 <keycode>' to make it known.
Nov  5 09:45:57 brian-laptop kernel: [  121.911104] atkbd.c: Unknown key released (translated set 2, code 0xf5 on isa0060/serio0).
Nov  5 09:45:57 brian-laptop kernel: [  121.911119] atkbd.c: Use 'setkeycodes e075 <keycode>' to make it known.
Nov  5 09:46:03 brian-laptop kernel: [  127.016585] atkbd.c: Unknown key pressed (translated set 2, code 0xf5 on isa0060/serio0).
Nov  5 09:46:03 brian-laptop kernel: [  127.016598] atkbd.c: Use 'setkeycodes e075 <keycode>' to make it known.
Nov  5 09:46:03 brian-laptop kernel: [  127.201324] atkbd.c: Unknown key released (translated set 2, code 0xf5 on isa0060/serio0).
Nov  5 09:46:03 brian-laptop kernel: [  127.201337] atkbd.c: Use 'setkeycodes e075 <keycode>' to make it known.
Nov  5 09:46:04 brian-laptop kernel: [  128.323493] atkbd.c: Unknown key pressed (translated set 2, code 0xf5 on isa0060/serio0).
Nov  5 09:46:04 brian-laptop kernel: [  128.323506] atkbd.c: Use 'setkeycodes e075 <keycode>' to make it known.
Nov  5 09:46:04 brian-laptop kernel: [  128.458524] atkbd.c: Unknown key released (translated set 2, code 0xf5 on isa0060/serio0).
Nov  5 09:46:04 brian-laptop kernel: [  128.458539] atkbd.c: Use 'setkeycodes e075 <keycode>' to make it known.


After I setkeycodes, xev did see the key pressed.

Thanks!

---

### Post by gianluca.colucci on 2008-11-06
Ok, can someone explain it to me now :) ?

I was getting the same message in dmesg. I understood that it was missing some kind of mapping between the keycode and the actual key. Fine, I typed sudo setkeycodes e075 235 and it has stopped. 

Now, I can press fn+f2 --> f12 and I don't get any error in the dmesg.

However, nothing changes, no audio, no brightness, etc.


Can someone explain me what I am missing?

Erm.. PS: I have removed fsfn. Was it necessary?

PS 2: I have tried to run again fsfn but I cannot see it either with a ps aux | grep fsfn nor a lsmod | grep fsfn. Something wrong?

Thanks again,
G. 

Thanks for this topic anyway.

Cheers,
Gian.

---

### Post by gianluca.colucci on 2008-11-06
Ok, I have found out what xev is :)

However, even after setting the keycode, if I try to press any fn + something else, I get always the same response from xev:

```

KeyRelease event, serial 34, synthetic NO, window 0x3600001,
    root 0x89, subw 0x0, time 2257325, (394,53), root:(401,644),
    state 0x0, keycode 74 (keysym 0xffc5, F8), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x3600001,
    root 0x89, subw 0x0, time 2258813, (394,53), root:(401,644),
    state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

is this normal?!

Cheers,
G.

---

### Post by gianluca.colucci on 2008-11-06
Ok, sorry guys.

I have seen now that the keycodes of the bit of xev output I post were changing. So I have tried again and here the result:

**[SIZE="3"]F1[/SIZE]**
```

KeyRelease event, serial 34, synthetic NO, window 0x3600001,
    root 0x89, subw 0x0, time 2257325, (394,53), root:(401,644),
    state 0x0, keycode 74 (keysym 0xffc5, F8), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x3600001,
    root 0x89, subw 0x0, time 2258813, (394,53), root:(401,644),
    state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

```


**[SIZE="3"]F2, F3, F4, F5, F6, F7, F10, F12[/SIZE]**

```

KeyPress event, serial 34, synthetic NO, window 0x3c00001,
    root 0x89, subw 0x0, time 2965676, (392,16), root:(399,607),
    state 0x0, keycode 243 (keysym 0x1008ff5b, XF86Documents), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x3c00001,
    root 0x89, subw 0x0, time 2965758, (392,16), root:(399,607),
    state 0x0, keycode 243 (keysym 0x1008ff5b, XF86Documents), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

...F8, F9 AND F11 have other different codes..

Any ideas?

Thanks,
Gian.

---

### Post by ingegnerlillo on 2008-11-20
I've tried sudo setkeycodes e075 235 but xev doesn't recognize anything when fn key is pressed...

Some ideas?

Sony vaio Vgn-fs115s

Edit: ok, i'm a stupid...

This is what appen:

xev | grep -A2 --line-buffered '^KeyRelease' | sed -n '/keycode /s/^.*keycode \([0-9]*\).* (.*, \(.*\)).*$/\1 \2/p'

every fn + f2-f3-f4-f5-f6-f7-f10-f12 generates

243 XF86Documents

---

### Post by Camilia on 2008-11-20
I very rarely use the function keys on my computer. Why do you need to use the functions keys?

---

### Post by ingegnerlillo on 2008-11-20
To increase, decrease volume in full screen mode, for example...

Or to increase, decrease brightness...

---

### Post by Yezinki on 2008-11-20
Only F2 setup shall function correctly.

---

### Post by prashantv on 2008-11-28
I have the same issue - FN keys do not work in Ubuntu 8.10 and fsfn does not work either.

I got sick of writing to the backlight file everytime I needed to change the brightness, so I managed to hack together a temporary solution that works for me. Details here:
[http://blog.prashantv.com/2008/vaio-fs-fn-keys-ubuntu-810/](http://blog.prashantv.com/2008/vaio-fs-fn-keys-ubuntu-810/)

It's not really easy to follow - you need to understand how linux works to follow it. Unfortunately, I don't have the time to make it nice and generic for everyone or to create a nice package. I just wanted something quick that would work.

---

### Post by bapar on 2008-12-28
I have installed Ubuntu this week for the first time and as a long-time Windows user I am very impressed with it.  I even wiped Windows off my hard drive after trialling it for a while.  However, I have searched all the threads trying to get my laptop's function keys to work. I have followed several different  instructions for earlier versions of Ubuntu that seemed easy enough to follow but they did not work. 

I don't really need to adjust volume or hibernate, but I do use the function keys regularly for brightness control, and sometimes to zoom and attach a monitor for presentations.  I would be grateful for any advice on how to fix this.

I have the model VGN-FS25GP and really think it's a beaut laptop.  I am using Ubuntu 8.10.

---

### Post by ingegnerlillo on 2009-01-07
> **prashantv said:**
> I have the same issue - FN keys do not work in Ubuntu 8.10 and fsfn does not work either.

I got sick of writing to the backlight file everytime I needed to change the brightness, so I managed to hack together a temporary solution that works for me. Details here:
[http://blog.prashantv.com/2008/vaio-fs-fn-keys-ubuntu-810/](http://blog.prashantv.com/2008/vaio-fs-fn-keys-ubuntu-810/)

It's not really easy to follow - you need to understand how linux works to follow it. Unfortunately, I don't have the time to make it nice and generic for everyone or to create a nice package. I just wanted something quick that would work.

Thank you so much, with some "easy" modifications it works very well for me.

I don't know why but I can't execute setkeycodes as user, so I put it in /etc/gdm/Init/Default, xbindkeys on gnome-session startup and I finally have my fn keys working!

P.S.: I've tried to leave a comment on you website, but it kept on saying that email address is not valid...

---


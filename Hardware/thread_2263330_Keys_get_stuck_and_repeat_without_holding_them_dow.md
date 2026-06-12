---
title: "Keys get stuck and repeat without holding them down"
date: 2015-01-31
forum: Hardware
---

### Post by Gijsbert_Wiesenekk on 2015-01-31
Hi,

I am running Ubuntu 14.04 on a Dell Precision M4800. Since a couple of weeks I am having the problem that keys sometimes get stuck and repeat without holding them down. This can happen for any key, just hitting a key once quickly can result in this:

[FONT=courier new]```
gwies@precm4800:~$ aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
gwies@precm4800:~$ 000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
```

[/FONT]Hitting Control-C or the key again stops the repeat. This is especially annoying if the Enter key gets stuck.. I have researched the Internet but could not find a workaround.

Any ideas?
Gijsbert

---

### Post by Gijsbert_Wiesenekk on 2015-02-01
The XeV output is as follows:

Pressing the 'a' key a couple of times:

```
KeyPress event, serial 37, synthetic NO, window 0x4200001,
root 0xaa, subw 0x0, time 40045875, (93,47), root1621,99),
state 0x10, keycode 38 (keysym 0x61, a), same_screen YES,
XLookupString gives 1 bytes: (61) "a"
XmbLookupString gives 1 bytes: (61) "a"
XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x4200001,
root 0xaa, subw 0x0, time 40045906, (93,47), root1621,99),
state 0x10, keycode 38 (keysym 0x61, a), same_screen YES,
XLookupString gives 1 bytes: (61) "a"
XFilterEvent returns: False

KeyPress event, serial 37, synthetic NO, window 0x4200001,
root 0xaa, subw 0x0, time 40046602, (93,47), root1621,99),
state 0x10, keycode 38 (keysym 0x61, a), same_screen YES,
XLookupString gives 1 bytes: (61) "a"
XmbLookupString gives 1 bytes: (61) "a"
XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x4200001,
root 0xaa, subw 0x0, time 40046639, (93,47), root1621,99),
state 0x10, keycode 38 (keysym 0x61, a), same_screen YES,
XLookupString gives 1 bytes: (61) "a"
XFilterEvent returns: False

KeyPress event, serial 37, synthetic NO, window 0x4200001,
root 0xaa, subw 0x0, time 40047328, (93,47), root1621,99),
state 0x10, keycode 38 (keysym 0x61, a), same_screen YES,
XLookupString gives 1 bytes: (61) "a"
XmbLookupString gives 1 bytes: (61) "a"
XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x4200001,
root 0xaa, subw 0x0, time 40047829, (93,47), root1621,99),
state 0x10, keycode 38 (keysym 0x61, a), same_screen YES,
XLookupString gives 1 bytes: (61) "a"
XFilterEvent returns: False
```

Now the key starts to repeat itself as you can see from the timestamps:

```
KeyPress event, serial 37, synthetic NO, window 0x4200001,
root 0xaa, subw 0x0, time 40047829, (93,47), root1621,99),
state 0x10, keycode 38 (keysym 0x61, a), same_screen YES,
XLookupString gives 1 bytes: (61) "a"
XmbLookupString gives 1 bytes: (61) "a"
XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x4200001,
root 0xaa, subw 0x0, time 40047859, (93,47), root1621,99),
state 0x10, keycode 38 (keysym 0x61, a), same_screen YES,
XLookupString gives 1 bytes: (61) "a"
XFilterEvent returns: False

KeyPress event, serial 37, synthetic NO, window 0x4200001,
root 0xaa, subw 0x0, time 40047859, (93,47), root1621,99),
state 0x10, keycode 38 (keysym 0x61, a), same_screen YES,
XLookupString gives 1 bytes: (61) "a"
XmbLookupString gives 1 bytes: (61) "a"
XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x4200001,
root 0xaa, subw 0x0, time 40047890, (93,47), root1621,99),
state 0x10, keycode 38 (keysym 0x61, a), same_screen YES,
XLookupString gives 1 bytes: (61) "a"
XFilterEvent returns: False

KeyPress event, serial 37, synthetic NO, window 0x4200001,
root 0xaa, subw 0x0, time 40047890, (93,47), root1621,99),
state 0x10, keycode 38 (keysym 0x61, a), same_screen YES,
XLookupString gives 1 bytes: (61) "a"
XmbLookupString gives 1 bytes: (61) "a"
XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x4200001,
root 0xaa, subw 0x0, time 40047921, (93,47), root1621,99),
state 0x10, keycode 38 (keysym 0x61, a), same_screen YES,
XLookupString gives 1 bytes: (61) "a"
XFilterEvent returns: False
```

The KeyPress event immediately follows the KeyRelease event.

Any suggestions?
Gijsbert

---

### Post by Gijsbert_Wiesenekk on 2015-02-01
Disabling 'Repeat Keys' in the 'Typing' section of the 'Keyboard' settings showed me the root cause, as suddenly some key-presses did not seem to get through while typing. The XeV output is:

```
KeyPress event, serial 37, synthetic NO, window 0x4800001,
    root 0xaa, subw 0x0, time 45235394, (99,97), root:(1384,287),
    state 0x10, keycode 38 (keysym 0x61, a), same_screen YES,
    XLookupString gives 1 bytes: (61) "a"
    XmbLookupString gives 1 bytes: (61) "a"
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x4800001,
    root 0xaa, subw 0x0, time 45235432, (99,97), root:(1384,287),
    state 0x10, keycode 38 (keysym 0x61, a), same_screen YES,
    XLookupString gives 1 bytes: (61) "a"
    XFilterEvent returns: False

KeyPress event, serial 37, synthetic NO, window 0x4800001,
    root 0xaa, subw 0x0, time 45237202, (99,97), root:(1384,287),
    state 0x10, keycode 38 (keysym 0x61, a), same_screen YES,
    XLookupString gives 1 bytes: (61) "a"
    XmbLookupString gives 1 bytes: (61) "a"
    XFilterEvent returns: False
```

The KeyRelease event is not sent, triggering the repeat. 

Any ideas?
Gijsbert

---

### Post by Gijsbert_Wiesenekk on 2015-02-01
Perhaps the issue is specific for the Dell Precision M4800, see:

[http://askubuntu.com/questions/567269/fast-pressed-key-triggers-auto-repeat-ubuntu-14-04-lts](http://askubuntu.com/questions/567269/fast-pressed-key-triggers-auto-repeat-ubuntu-14-04-lts)

Gijsbert

---

### Post by Gijsbert_Wiesenekk on 2015-02-01
It starts to look like a hardware problem. I tried different desktop environments to no avail. I just reinstalled Ubuntu 14.04 but I am having the same issue.

Gijsbert

---

### Post by bapoumba on 2015-02-01
Would you have another keyboard you could try (is this a laptop ?) ?

---

### Post by Gijsbert_Wiesenekk on 2015-02-11
I installed a new keyboard from Dell and that almost solved the issue, only one key got stuck occasionally. The root cause turns out to be the BIOS (in combination with the normal wear-and-tear of the keyboard).
Check out the release notes of BIOS version A13..

Gijsbert

---


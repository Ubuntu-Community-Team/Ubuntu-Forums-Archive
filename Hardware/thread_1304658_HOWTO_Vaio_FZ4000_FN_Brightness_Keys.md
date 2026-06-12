---
title: "HOWTO: Vaio FZ4000 FN Brightness Keys"
date: 2009-10-29
forum: Hardware
---

### Post by matts12290 on 2009-10-29
Most posts about changing the brightness on a Sony Vaio (I have an FZ4000) refer to installing spicctrl or nvclock and then using those settings to change it, but in Karmic Koala, you can just install the recommended video driver and use the smartdimmer command.

Usage: smartdimmer [OPTION]...

Options:
-g --get Query brightness level.
-s --set <level> Set brightness level (15-100)
-i --increase Increase brightness with one level.
-d --decrease Decrease brightness with one level.
-h --help Prints this help text.

So first I made files for the brightness up and down settings:

```
$ sudo gedit /etc/acpi/events/sony-brightness-down
```

Then add the following code into that file:

```
event=sony/hotkey SNC 00000001 00000010
action=smartdimmer -d
```

Next you need to do the same but for the brightness up file.

```
$ sudo gedit /etc/acpi/events/sony-brightness-up
```

```
event=sony/hotkey SNC 00000001 00000011
action=smartdimmer -i
```

Now the keys have binds and all you need to do is restart the acpid

```
$ sudo restart acpid
```


Now you should have working brightness up/down keys for your Vaio.

---


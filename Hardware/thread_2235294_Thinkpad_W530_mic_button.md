---
title: "Thinkpad W530 mic button"
date: 2014-07-20
forum: Hardware
---

### Post by cpdondo on 2014-07-20
Has anyone gotten the mic mute button on a lenovo thinkpd W530 recognized by acpi?

acpi_listen ignores it completely.  xev sees it and returns

MappingNotify event, serial 41, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

which tells me nothing useful.

There's a patch floating around to enable the LED, but without activating the button the LED won't do me any good.

---


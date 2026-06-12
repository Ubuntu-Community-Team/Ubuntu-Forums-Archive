---
title: "Thinkpad x200s, 9.04: volume buttons stopped working, but OSD still shows"
date: 2009-11-16
forum: Hardware
---

### Post by rduke15 on 2009-11-16
Many people seem to have various problems with the Thinkpad's volume control, but they all seem to be different problems.

On my x200s with Jaunty 9.04, the volume keys used to work as expected: they changed the volume, and the OSD notification showed. But since a week or 2, something changed, and the status is now:

- **the volume buttons don't change the volume**, even though the OSD still appears and the slider in it does move.

- the mute button still works, but there is no OSD notification
- the software volume control still works as expected


* In gconf-editor:

- /apps/gnome-volume-control/active-element = HDA Intel (Alsa mixer)

- /apps/gnome_settings_daemon/keybindings/volume_down = XF86AudioLowerVolume
- /apps/gnome_settings_daemon/keybindings/volume_up = XF86AudioRaiseVolume
- /apps/gnome_settings_daemon/keybindings/volume_mute = XF86AudioMute

- /schemas/apps/gnome-volume-control is empty

* acpi-listen results :

- no events for volume keys (but the OSD shows, so the keys must be handled by something else)
- no event for the mute key, which works, but without OSD
- events for the brightness control keys which work as expected

* /proc/acpi/ibm/ :

"echo mute >/proc/acpi/ibm/volume" works
"echo up >/proc/acpi/ibm/volume" does un-mute, does change the level shown by "cat /proc/acpi/ibm/volume", but [B]doesn't actually change the volume
[/B]
"echo reset >/proc/acpi/ibm/hotkey" or "echo reset >/proc/acpi/ibm/hotkey" do change the values shown by cat /proc/acpi/ibm/hotkey, but don't change the behavior.

I don't know what to check/try next. These volume keys used to work when I had freshly installed Jaunty a couple of months ago. Now they don't anymore, and I don't have a clue about what may have broken it.

Thanks for any help...

RD

---

### Post by rduke15 on 2009-11-25
Bump...?

---


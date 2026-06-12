---
title: "iBook G4 still missing sound, wireless"
date: 2010-02-01
forum: Hardware
---

### Post by Boogerhead on 2010-02-01
Kind folks,

I tried to do some research and tried quite a few things, but a fresh install of 9.10 PPC just ain't getting anywhere.

I ran all updates, restarted a few times, no joy.

Wireless: uses b43-fwcutter. Installed via Synaptic Package Manager; when asked, checked box to download firmware; finished install; restarted; nothing showing under network icon. Uninstalled. Ran apt-get command-line, ran to get the firmware, same thing. Followed fwcutter directions to manually download files, manually extract firmware to /lib/firmware; about 30 files kicked  out; restarted; nothing. iwconfig shows lo, eth0, pan0; I think pan0 is Bluetooth. "no wireless extension" shows after each entry. modprobe -l shows a b43 extension. I don't know where else to look or poke or try. ... Could there be a firmware difference with PowerPC?

Sound: I haven't fiddled with as much. I was going off the PowerPCFAQ, and saw I was supposed to add something to /etc/modules, which already had three things: snd_powermac, apm_emu, snd-powermac. No sound hardware is listed in System: Preferences: Sound. I get no sound.

Any ideas? If y'all can steer me toward the right HOWTO or whatever, that'd be fine -- but I've exhausted the documentation I can find.

---

### Post by Boogerhead on 2010-02-01
And on an utterly unrelated note: Any idea how I can work around a printer driver? I've got a Canon Pixma MX330, but the only DEB packages I can find are for i386, this is a PPC.

---

### Post by Boogerhead on 2010-02-02
> **Boogerhead said:**
> And on an utterly unrelated note: Any idea how I can work around a printer driver? I've got a Canon Pixma MX330, but the only DEB packages I can find are for i386, this is a PPC.

I think I've got a way around this (extract the PPD from the i386 DEB or the Mac files), but still need ideas for the wireless and sound. Anyone?

---


---
title: "Radeon 6670"
date: 2013-10-10
forum: Hardware
---

### Post by madahlke27 on 2013-10-10
I recently tried to update my Radeon 6670 driver with the lines in the terminal...

```

[FONT=Ubuntu Mono]sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
[/FONT]sudo apt-get update 
sudo apt-get upgrade [FONT=Ubuntu Mono]sudo apt-get install fglrx
[/FONT]
```

When rebooting all was well until after the the Ubuntu Logo part when all I saw was on my monitors was this...

[IMG]https://lh6.googleusercontent.com/-GpWkyAvakCk/Ulb40e2vAnI/AAAAAAAAR5g/V3MZR-CTkhw/w755-h566-no/IMG_20131010_135836.jpg[/IMG]

I tried to enter recovery mode and remove "apt-get remove fglrx" but it always returned an error saying there were dependencies

I tried to boot in fail safe graphics mode and that also did not work.

I have no idea what I can do short of reinstalling linux to get my machine back up and running.

Any help is greatly appreciated

PS - any errors you need let me know and I will post them.
PSS - please keep in mind I have been using linux (Ubuntu specifically) for just over a month now.


:: UPDATE ::
I found a post with the following information...

```

**Workaround C: Disable the VESA framebuffer from grub**

[COLOR=#333333][FONT=Ubuntu Beta]The linux kernel uses the framebuffer for doing graphics prior to X starting up. 
For systems that support Kernel Mode Setting (KMS), this includes using the higher resolutions of the video card. 
The kernel uses a framebuffer driver for this, such as -vesafb. However this can misbehave sometimes (e.g. hardware-specific bugs).
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]You can disable vesafb in grub by passing it a nonsensical parameter. E.g.:[/FONT][/COLOR]

[LIST]
[*]vesafb.nonsense=1
[/LIST]

```

This worked and I was able to boot but I don't know why it worked and I don't know if it will continue to work.

Any thoughts?

---

### Post by mkmanifesto on 2013-10-11
Did you try to purge the install?

```
apt-get purge fglrx
```

---


---
title: "Trouble with Compiz-Fusion in Ubuntu 7.10"
date: 2008-08-20
forum: General Help
---

### Post by junojpeg on 2008-08-20
I am currently running Ubuntu 7.10 within Windows from a USB Flash Drive with Qemu Hardware Emulator. When I run Ubuntu In this manner, I cannot figure out how to run Compiz-Fusion, even though Synaptic Package Manager says that it is already installed. Any suggestions?

---

### Post by mb_webguy on 2008-08-20
Well, there are several potential problems here, but...

Do you have the compizconfig-settings-manager package installed?

---

### Post by junojpeg on 2008-08-20
Yes

---

### Post by mb_webguy on 2008-08-20
And I guess you went to System->Preferences->Appearance, clicked on the Visual Effects tab, and selected Extra...?

Sorry if this is a bit basic, but it's amazing how often people overlook the little things.

---

### Post by junojpeg on 2008-08-20
Every time I select extra, Ubuntu says it cannot be activated...

---

### Post by mb_webguy on 2008-08-20
I was afraid of that.  Most virtual machines and emulators don't do well with graphics, since it doesn't allow direct access to the video card.  That's actually the main reason I've never had much use for them, since the programs that I'd be most likely to use an emulator or VM to run (e.g. games) are fairly graphics-intensive.

However, it could still be a video driver problem.  What kind of video card do you have, and what kind of video card is Qemu emulating?

---


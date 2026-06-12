---
title: "Problem upgrading from 8.10 to 9.04 (not booting anymore)"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by daniel_gv93 on 2009-04-24
I need help, i was upgrading ubuntu intrepid to jaunty with the manager.. but i forgot and turned the machine off in the middle of the process(when it was downloading the new version) then i tried to boot and i only loaded the "ubuntu studio" bar then only the cursor is visible.:confused::(
Just to clarify, i dont have ubuntu studio, i installed ubuntu then installed the ubuntu studio packages from the repository.
All help will be appreciated.

---

### Post by Roger E Critchlow Jr on 2009-04-24
Hi --

Bad move, but it sounds like you can boot, despite the title you wrote -- how can you see something that says Ubuntu Studio if you didn't boot?

So switch into a console with Ctrl-Alt-F1 (or boot into recovery mode) and then execute:

[INDENT]sudo apt-get update
sudo apt-get upgrade
[/INDENT]
If you get some message about package damage that instructs you to run some dpkg command, do that and try again.

With luck, the package manager will be able to recover for you.

-- rec --

---

### Post by daniel_gv93 on 2009-04-28
ok, ill try it :P thank you ill let you know if it worked

---

### Post by daniel_gv93 on 2009-04-28
ok, so i did that and it worked:D:D but then when i try to boot again it does in text mode and it says:

Error:AFI mismatch: the NVIDIA kernel module has version 180.44,
but this NVIDIA driver component has version 180.11. Please make sure that the kernel module and all NVIDIA driver components have the same version.

I have nVIDIA GeForce 7300LE. I dont know what to do :S.

---

### Post by Roger E Critchlow Jr on 2009-04-29
Okay, the current version of nvidia-180-kernel-source is 180.44-0ubuntu1, which matches the message you got.

I'd try to reinstall the other version 180 nvidia driver packages, so, from the text console:

[INDENT]sudo apt-get --reinstall install nvidia-glx-180 nvidia-180-modaliases
[/INDENT]
The version 180 nvidia is the correct driver for the GeForce 7300 LE.  I don't know why they move the version number around in the package name.

Oh, you might try a

[INDENT]sudo apt-get check
[/INDENT]
to see if apt can find any other damage to correct, too.  See how that goes.

-- rec --

---


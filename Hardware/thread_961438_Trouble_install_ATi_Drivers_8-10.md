---
title: "Trouble install ATi Drivers 8-10"
date: 2008-10-28
forum: Hardware
---

### Post by KDB9000 on 2008-10-28
I am trying to install 8-10 ATi drivers into my laptop that has a Radeon Xpress 200M. I got the last version to work and then did a kernel upgrade and it broke the ATi drivers. Now I am trying to reinstall them so I can have direct rendering. Here is the install log:


Creating symlink /var/lib/dkms/fglrx/8.542/source ->
                 /usr/src/fglrx-8.542

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
pushd /var/lib/dkms/fglrx/8.542/build; sh make.sh --nohints; popd.....
[Error] Kernel Module : Failed to build fglrx-8.542 with DKMS
[Error] Kernel Module : Removing fglrx-8.542 from DKMS

So I tried to build the DEB files and this is what I get:

Generating package: Ubuntu/hardy
Resolving build dependencies...
Unable to resolve  can't parse dependency ooobasis30-en_us-res
 can't parse dependency ooobasis30-en_us-help
 can't parse dependency ooobasis30-en_us
 can't parse dependency ooobasis30-en_us-base
 can't parse dependency ooobasis30-en_us-binfilter
 can't parse dependency ooobasis30-en_us-math
 can't parse dependency ooobasis30-en_us-calc
 can't parse dependency ooobasis30-en_us-impress
 can't parse dependency ooobasis30-en_us-draw
 can't parse dependency ooobasis30-en_us-writer.  Please manually install and try again.
Signal caught, cleaning up

The Signal Caught is mean pressing Ctrl-C. Anyone have any thoughts on this?

---

### Post by antez on 2008-10-28
same here, but in my desktop and gess what I have wireless internet and i can't update it. can I tern it to falesafe grafics for same reassson?:confused:

---

### Post by KDB9000 on 2008-10-29
Bump?

I do have Open Office 3 install and would like to keep it since Ubuntu hasn't made a package for Open Office 3 yet (at least for 8.04). Anyone have any ideas? I found some "fixes" but they didn't work.

---


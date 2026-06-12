---
title: "Couldn't find task ubuntustudio-*"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by thereisor on 2009-05-01
I got caught with my pants down running 7.10, and support got dropped on the 18th, so now I'm scrambling to install 8.04.1.  I'm using tftpboot, since I lack a dvd rom.  When the installer gets to the package installation section, it fails.

A look at the other console shows the errors:

```

Couldn't find task ubuntustudio-audio
Couldn't find task ubuntustudio-audio-plugins
Couldn't find task ubuntustudio-desktop
Couldn't find task ubuntustudio-graphics
Couldn't find task ubuntustudio-video

```Is there, perhaps, and alternate mirror I should be using?  I was using us.archive.ubuntu.com.

I suppose I could just de-select the packages in question and grab them afterward.  This is what I did for 7.10, and it always bugged me that I had to do it that way.

---

### Post by thereisor on 2009-05-01
One acceptable alternative would be to be able to supply an NFS share for packages.  Then I could mount -o loop the iso and then share the mount point.

But I haven't found a way to configure the installer to point to an NFS share.

---

### Post by thereisor on 2009-05-02
Well, I see now what the problem is, as reported here:

[https://bugs.launchpad.net/ubuntu/+source/base-installer/+bug/199649](https://bugs.launchpad.net/ubuntu/+source/base-installer/+bug/199649)

"can't do network installations of tasks in universe"

---


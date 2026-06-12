---
title: "ATI CCC Adminstrative Lockout"
date: 2009-11-04
forum: Hardware
---

### Post by Intel91 on 2009-11-04
I am trying to adjust my resolution in CCC and every time I click on ATI CCC (Administrative) it returns an error message: "Could not launch 'ATI Catalyst Control Center (Administrative)' - Failed to execute child process "amdxdg-su" (No such file or directory)"

So, any help would be appreciated, as my current mode is 1024x768 as opposed to 1280x800, so the difference is annoying. It may be worth mentioning that under the Ubuntu natural drivers my resolution changes just fine up to 1280, however I don't have 3D acceleration.

Thanks,
Intel

---

### Post by Intel91 on 2009-11-04
Solved it. Just go to the terminal, type gedit /etc/X11/xorg.conf and add the following info bellow Sections Screens:
SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection

That is, replacing the resolution with the one you want.
I then went to System>Preferences>Display and turned off Mirror Screens, then selected 1280x800 then restarted.

---


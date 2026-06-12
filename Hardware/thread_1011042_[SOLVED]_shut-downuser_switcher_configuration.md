---
title: "[SOLVED] shut-down/user switcher configuration?"
date: 2008-12-14
forum: Hardware
---

### Post by scradock on 2008-12-14
Can anyone tell me where the "new" user switcher/shutdown combination panel applet is configured? Specifically, I cannot use the "suspend" option from the panel because some inappropriate --quirks are included - I just need to edit the config to remove them. But I can't find the relevant config file - it isn't in the places I've looked based on "man pm-suspend", for instance.

If I just issue the command "sudo pm-suspend" in a terminal suspend works fine and the video resumes correctly; using the panel applet the machine suspends but will not resume correctly, probably because the video-post quirk is set when it shouldn't be. But where??????

---

### Post by scradock on 2008-12-16
Well, no-one responded, so I poked around and found out.

The suspend operation in power-manager (now merged with the fast-user-switcher) is now configured in /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux. This appears NOT to be documented anywhere within the Intrepid install - all Help and man pages refer to older arrangements.

HAL now has a database that tells it what video-quirks are appropriate for various machines; mine is not listed, so HAL tries using a subset of the available quirks that "might work for older systems."

This is not what my system needs - it needs no quirks at all, it seems. The quirks used are listed at the start of /var/log/pm-suspend.log, and I was able to find the list that sets them on in the file ....../hal-system-power-suspend-linux. I set them all to false, instead of true, and suspend now works correctly.

Hope that helps someone else sort this out - every system will be different, of course, so your solution will differ from mine......

---


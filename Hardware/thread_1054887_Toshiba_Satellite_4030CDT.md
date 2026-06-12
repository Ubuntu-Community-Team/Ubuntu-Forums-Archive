---
title: "Toshiba Satellite 4030CDT"
date: 2009-01-30
forum: Hardware
---

### Post by theprofessor13 on 2009-01-30
Hi everyone

This is my first post here and my first real attempt at using Linux so go easy on me ;).

So I've got my old Toshiba 4030CDT out and decided to install Xubuntu 8.10 on it. Everything is running fine and even fast. Not as fast as my Core i7, or when the laptop was running XP but fast none the less. Except for the display. I can run at 800x600x24 but not 1024x768x16. I would much prefer the extra screen real estate than the extra colours :). I could do it with Windows XP but for the life of me can not figure out how to do it under Linux. Any help would be greatly appreciated.

---

### Post by 73ckn797 on 2009-01-30
> **theprofessor13 said:**
> Hi everyone

This is my first post here and my first real attempt at using Linux so go easy on me ;).

So I've got my old Toshiba 4030CDT out and decided to install Linux on it. Everything is running fine and even fast. Not as fast as my Core i7 or when it was running XP but fast none the less. Except for the display. I can run at 800x600x24 but not 1024x768x16. I would much prefer the extra screen real estate than the extra colours :). I could do it with Windows XP but for the life of me can not figure out how to do it under Linux. Any help would be greatly appreciated.


Did you check System/Administration/Hardware Drivers to see whether there are any restricted drivers available for the video?

---

### Post by theprofessor13 on 2009-01-30
I haven't yet, but I'll have a look.

Thanks for the reply :).

Edit:
OK, because I am using Xubuntu, there is no "System/Administration/Hardware Drivers". It's just "System/Hardware Drivers".
Anyway, the Hardware Drivers window pops up and in it it says "No Proprietary Drivers are in use on the System". I don't see anywhere to check for driver updates in the window either :(.

---

### Post by 73ckn797 on 2009-01-30
> **theprofessor13 said:**
> I haven't yet, but I'll have a look.

Thanks for the reply :).

Edit:
OK, because I am using Xubuntu, there is no "System/Administration/Hardware Drivers". It's just "System/Hardware Drivers".
Anyway, the Hardware Drivers window pops up and in it it says "No Proprietary Drivers are in use on the System". I don't see anywhere to check for driver updates in the window either :(.

I am not familiar with Xubuntu all that much. Look around the forums as I am sure there are other posts that have addressed your particular situation. Maybe post your question in the video forum.

---

### Post by theprofessor13 on 2009-01-30
I was going to post in the "Multimedia and Video" section but I places it here as it was an issue with a laptop. The sub-sections need to be less broad. We have the same issue over at nVidia Forums.

Anyway, thanks for your help :). Any suggestions on what I should search for? I'm not all that fluent in the Linux "lingo". I own Windows though.

---

### Post by 73ckn797 on 2009-01-30
Go into System/Administration/Software Sources and enable the restricted (multiverse) repositories. Then reload as directed and then use System/Administration/Update Manager to check for more updates. It may then give you notice of restricted video drivers to install. If there is a "recommended" driver, use that one. If that is the case and you install it you will probably have to restart the computer for it to take effect. 

See how that will work.
 I will look here later today to see any response.

---

### Post by theprofessor13 on 2009-01-30
OK, I went into "Applications/System/Software Sources" but the "restricted (multiverse) repositories" option was already enabled.
I'm checking the updates list now. It might take a while as there are 161 of them.

Edit:
Apparently my system is up to date. I know this isn't right as just last night I disabled automatic update downloading and installing as it was to resource intensive (mouse lag:()and there were 161 updates. I can now not get back into the updater's preferences to re-enable automatic download and installation.

Any ideas?

---

### Post by theprofessor13 on 2009-01-31
Bump. It's been a day and this is already on page 9 :O.

---


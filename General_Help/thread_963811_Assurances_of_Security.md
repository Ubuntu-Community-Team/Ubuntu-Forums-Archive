---
title: "Assurances of Security"
date: 2008-10-30
forum: General Help
---

### Post by Mizutsuki on 2008-10-30
An organization recently asked me if I could figure out how to set up their computers for them in such a way that they could be sure the systems were secure.  They had a number of criteria, but essentially it boiled down to "Don't let anything stay on the hard drives because someone will install spyware, or someone will accidentally leave sensative documents."
8.10 has the new Guest feature, and we'll probably use that but I was thinking as an additional precaution it'd be great if we could do ubuntu onto a read-only hard drive, and then have the /home directory on a RAM drive that would be gone every time the computer restarted.  I just mainly wanted to know if anyone had ever done anything like this before and how I might go about assuring that nobody screwed with it.
The other question I had about this is, is there some really easy way to log people off if they've been idle for 5 minutes, and, in so doing, wipe the home dir?

Thanks so much to all.

---

### Post by cdenley on 2008-10-30
You can delete everything in /home, mount it as tmpfs, then configure pam to create user directories if they don't exist. I've done that before and it worked well.

I also managed to make the entire filesystem read-only.
[http://ubuntuforums.org/showpost.php?p=5720661&postcount=5](http://ubuntuforums.org/showpost.php?p=5720661&postcount=5)

Both solutions will allow the users to make changes, but the changes are actually stored in memory, and everything will be rolled back when the computer is rebooted. Just keep in mind that if you make a lot of changes, you are going to use a lot of your memory.

With the second solution, you have to mount the filesystem with a livecd if you want to change anything for real, like making the filesystem writeable again.

---

### Post by snowpine on 2008-10-30
Just run Linux from a Live CD on a computer with no hard drive, problem solved.

---

### Post by cdenley on 2008-10-30
> **snowpine said:**
> Just run Linux from a Live CD on a computer with no hard drive, problem solved.

Except for the poor performance, and lack of security updates. I would suggest the first solution I gave. Non-admin users shouldn't have privileges to write anything outside of /home, and admin users can install software, change settings, etc.

---


---
title: "Have I got it right till now?"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by dE_logics on 2009-04-06
While installation, the drive specified as '/' is the root directory, where everything needs to be installed.

Now apart from this, we can mount other directories as /bin, /user etc...

So after installation, if I open my root directory, it contains  /bin, /user despite the fact that I specified different directories for each of them; but actually the reside on a different drive.

Am I right till now?

Now the drives which I mounted as /bin, /user...can they be accessible via the location 'Computer' (in gnome)...if they are accessible, can I put other files in these directories, or use them for other purposes?

Can I specify 2 directories as /bin, /user?

Can I mount sub directories to a different drive...like /user/bin or user/include etc...

Suppose I did not mount certain partitions...will they not auto-mount on boot?

If I did not mount many directories as different partitions, will automatically get made in the '/' partition which I specified, i.e one partition with many mount points?

---

### Post by ajgreeny on 2009-04-06
If you choose to just use a / partition and swap at instalation time, everything will reside under /.  If you choose to have a separate /boot, /home, /etc, as some people do,particularly /home, all system use will be of the separate /home, though you will still see another /home in your file system, though that will be empty.  The same situation will occur if you have a separate /etc, and so on.  Don't worry about it, however, the system will still appear seamless in execution.

Personally I would just stick with a separate /home partition and forget about all the rest.  It makes life a lot easier when you do a system upgrade, eg from Intrepid to Jaunty.

---

### Post by dE_logics on 2009-04-06
More partitions convert to faster access times, moreover you can specify different file systems for that specific purpose...for instance resierFS to the boot partition since its optimized for handling small files.

Making a separate boot partition should make the boot process lightning.

So what if you wanna upgrade with such complex directory structure?...I mean just need to specify your old directory structure that all...right?

---

### Post by ajgreeny on 2009-04-06
> I mean just need to specify your old directory structure that all...right?I think so, yes.

---

### Post by dE_logics on 2009-04-06
Ok then thanks!

Few question as still left though.

---

### Post by dE_logics on 2009-04-06
You can see my similarly unanswered questions in physicsforums.

Anyway, I realized the inbuilt DEB installer, g-deb.

but how about a graphical deb to RPM and RPM to deb converter?

---


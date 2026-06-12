---
title: "New user needs help with hard drive accessability under Ubuntu 7.04"
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by keoth on 2007-07-05
Hi everybody,

This might be one of those really easy new user questions, but I haven't been able to figure it out from reading the wiki or the forums. I might just be looking in the wrong places, but at the moment I'm stuck.

The problem I'm having is fairly simple - I cant give myself permission to write to two of my hard drives. I'm running Ubuntu 7.04 on a Pentium 4 machine, and all seems to be going well enough. The two hard drives (a maxtor 80gb and a seagate 300gb) are recognized and mounted, and I have read access to both. I'd like to be able to modify some of my files on them, but they both belong to the ROOT account, and I cant change the permissions to give my account (the only one on the system) full access. 

I'm guessing that there's a simple answer... I just haven't been able to find it. Can anyone steer me in the right direction, or know what I have to do?

Thanks

---

### Post by reckless2k2 on 2007-07-05
you need to edit the /etc/fstab and put your user permissions on those directories. check out etc fstab and additional parameters and you'll be there. it's not hard. backup the fstab though just in case you blow something up you can restore the original in recovery mode without issue.

---

### Post by keoth on 2007-07-05
I'm trying to edit the fstab file, but its read only too... so its not letting me change anything. Am I missing something else? 

Also, for some reason, both hard drives are occasionally (but not always) telling me that the user is unknown, and still not letting me change permissions in their properties window.

---

### Post by reckless2k2 on 2007-07-05
yeah you're not using the sudo function to elevate your priviledges.

---

### Post by keoth on 2007-07-05
ok, I think Ive got it now. I used the NTFS config utility, and all is well. Thanks forums!

---


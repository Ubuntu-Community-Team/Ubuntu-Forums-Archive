---
title: "Mounting issues again lol but it is something I did and not sure how to fix"
date: 2009-03-15
forum: Hardware
---

### Post by Robert505189 on 2009-03-15
My 175 external mounts fine as long as I disconnected it properly from vista. What I did is right click on the mounted file  system>properties>Drive>settings>mount options at this point apparently I inputed an invalid command. now when I connect my external drive I get an error message stating that it is an invalid command how do I fix this with out being able to mount the drive to change the mount option command

---

### Post by taurus on 2009-03-15
Can you still mount it by hand from a terminal?

```
sudo fdisk -l
df -h
```

---

### Post by Robert505189 on 2009-03-15
I will try this when I get the chance long storyshotr but I work offshore and I happen to be cooking something I normally don't do. Thanks for the suggestion though I will reply later if it worked.

---

### Post by Robert505189 on 2009-03-15
I was able to mount manually. Which is amazing on its on because I constantly have trouble with the fact that the external I use is rarely ejected properly for MS comps and hardy then refuses to mount and I could not figure out quite how to force mount. Anyway that gave me the push I needed to get it right. I new to Gnu/linux and the Terminal isn't really a mystery but I am slow to get some things thanks for the help here is a link to the guide I used to for mounting partitions if any one else has my issues;)

[http://http://www.guidetotech.com/2008/12/mount-ntfs-fat32-windows-drive-in.html]("http://www.guidetotech.com/2008/12/mount-ntfs-fat32-windows-drive-in.html")]

---


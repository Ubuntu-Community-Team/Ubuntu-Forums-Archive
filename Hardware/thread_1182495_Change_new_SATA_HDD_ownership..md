---
title: "Change new SATA HDD ownership."
date: 2009-06-09
forum: Hardware
---

### Post by ArkticMud on 2009-06-09
Hello all, I have recently installed a new HDD in my Ubuntu PC, Its a 500GB SATA and I wish to use it for sharing files. I managed to get write permissions by going into users and groups then ticking the "mount user-space file permissions (FUSE)" First question is does this put my computers security at risk in any way?
 Second questions is how can I share the whole 500GB HDD, it says the owner is root, and I want to change it to the user "ubuntu" (origianl user name I know) How is this done?

Thanks!

---

### Post by Lampi on 2009-06-09
ownership is changed by terminal command chown

"man chown" will give you the details

if you want to change a directory to username ubuntu make sure this username exists, then it's "chown ubuntu /name/of/the/directory"

---

### Post by ArkticMud on 2009-06-09
Thanks [Lampi]("http://ubuntuforums.org/member.php?u=545030")!

---


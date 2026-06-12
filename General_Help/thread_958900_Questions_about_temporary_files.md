---
title: "Questions about temporary files"
date: 2008-10-25
forum: General Help
---

### Post by cooldog on 2008-10-25
Hi all,

I am just curious that where does Ubuntu put all the temporary files, for example, update installation files, it usually download a few hundred Mbs. I am wondering where does Ubuntu put them and if it deletes those files after installations or I have to do it manually.

Thanks!

---

### Post by geirha on 2008-10-25
When you update or install packages, it downloads them to /var/cache/apt/archives/ and they don't get deleted. You should run ```
sudo apt-get clean
``` to remove them, or do it from synaptic (I don't use synaptic much, but it probably has that option somewhere)

---


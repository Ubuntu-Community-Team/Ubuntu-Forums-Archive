---
title: "[SOLVED] sharing  /home"
date: 2008-07-20
forum: General Help
---

### Post by mick222 on 2008-07-20
I have ubuntu hardy on one partition and a separate home partition i installed opensuse  and used the same home partition which messsed up my ati drivers. Should i give suse its own home partition or will reinstalling the ati drivers solve the problem.Also will i run into conflicts as suse users Kde4.

---

### Post by dcstar on 2008-07-20
> **mick222 said:**
> I have ubuntu hardy on one partition and a separate home partition i installed opensuse  and used the same home partition which messsed up my ati drivers. Should i give suse its own home partition or will reinstalling the ati drivers solve the problem.Also will i run into conflicts as suse users Kde4.

Do not share /home partitions between distributions, they each assume sole control of it and can set things which cause incompatibilities (as you have experienced).

Put any shared data into a separate filesystem/directory outside of the the root /home.

---

### Post by mick222 on 2008-07-20
thx thought that how can i change suse's /home directory or would it be easier to remove and reinstall suse.

---

### Post by dcstar on 2008-07-20
> **mick222 said:**
> thx thought that how can i change suse's /home directory or would it be easier to remove and reinstall suse.

Boot up Ubuntu, mount the SUSE partition and create a /home directory (using sudo) in the SUSE root directory, then edit the SUSE /etc/fstab and comment out (or delete) the line that mounts the shared /home directory.

Next time you start SUSE it should use the new /home directory.

---

### Post by mick222 on 2008-07-20
thx just seen a post that claims it is alright to share home between distros, but i  have had three distros running at the same time with seperate homes with no problems .

---


---
title: "Need help mounting a partition on a 4TB harddrive"
date: 2016-04-08
forum: Hardware
---

### Post by vandend278 on 2016-04-08
Hey everyone I have a question and any help I could use,

recently put together a new machine and installed it with a 4TB hard drive. While I've installed everything correctly (so far) it's dual booting just fine both Windows 10 and Ubuntu 15.10. However it has 3 partitions. The Windows 10 is 1.5TB. The Ubuntu is 500GB. Both boot without any issues, except I cannot get that remaining drive to mount inside Ubuntu. I can get it to mount the Windows 10 one. Granted this was supposed to be a shared partition allowing both OSs to access the same info. When I am in the Windows 10 partition though, that partition that is supposed to be shared does mount. The initial install was done with Windows after I unlocked the hard drive I was able to create my partitions, after which I booted from USB and installed Ubuntu.

Any suggestions will help thank you.

---

### Post by oldfred on 2016-04-08
Did you use gpt, and then Windows only installs in UEFI mode?
Post this:
sudo parted -l

 MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

---


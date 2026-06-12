---
title: "Lenovo U450P freezes during boot every other time"
date: 2010-06-03
forum: Hardware
---

### Post by danielgruen on 2010-06-03
Hi,

I recently installed Ubuntu 10.04 on my Lenovo Ideapad U450P. After updating the Kernel to 2.6.33-02063303 everything, including the wireless, seems to be working fine.

The only issue is this: after selecting the correct entry in Grub and pressing enter, there will be a blinking cursor for a few seconds. I expect this is when ureadahead is reading all necessary data from the hard disk. For me, however, with about 50% probability either of the following happens

1) either the message "ureadahead main process (485) terminated with status 5" is displayed, following to which everything will boot fine

2) or the blinking cursor will stay forever, the system not reacting to anything; the only thing I can do then is a hard reboot, after which the system may or may not boot successfully

I'm not sure where to find information about what goes wrong in case 2 -- logs don't seem to show anything suspicious to me. Does anybody have similar issues or knows where to look any further? Is there a way of finding out what ureadahead is or is not doing in both cases?

Thanks!
Daniel

---


---
title: "Software RAID questions"
date: 2008-09-20
forum: General Help
---

### Post by Linux&amp;Gsus on 2008-09-20
If everything works out well then I should be able to get a new desktop soon(-ish). So far I plan to have 2 HDDs in it. I would like to mirror them (RAID 1) to get some sort of backup/protection against HDD failure. Since I don't want to shell out any money for a hardware RAID controller (don't suggest that, I simply don't have the money for that, not even thinking about the common suggestion of buying 2 identical controllers to make sure to have a backup in case the controller dies) I'm looking into software RAID. I did some research on that but still have some questions remaining. Hopefully someone here can answer them.

OK, so from what I understood, in order to boot properly, I need to have the directory /boot on a single drive, not included in the RAID. Is that correct? If so, how much space do I need for that?
But that would also mean that in case that HDD fails I can't boot anymore. What is in that directory? Can I, after installation finished, just copy that over to the other HDD as backup? Can I even have a equally sized partition there called, say, /boot_BAK and in case of failure rename that to /boot and then can boot again? Therefore how about GRUB? Is that RAIDed as well?

What am I doing with SWAP, would that be in the RAID as well or excluded from it?
This is not so much about if it makes sense to RAID /swap but if that is technically possible or not. Like with the /boot issue, from what I read. After all, if it's not included in the RAID what would I do with the space on the other drive. So, I could as well include that and have at least the feeling of using the disk space I bought. Or is there anything useful I could do with that 1GB of space?

How easy is it in general to rebuild a Software RAID, or RAID in general for that matter? Specially if not everything (like /boot) is existing on both disks?
After all, I try to get a backup against HDD failure and maybe a little performance boost during read intensive work. Is that a good approach to do that with a software RAID 1 or do I get too many disadvantages (which ones?) with that or is it even missing my goal? If so, what would be a better way of doing it?

Thanks for all help and suggestions.

---


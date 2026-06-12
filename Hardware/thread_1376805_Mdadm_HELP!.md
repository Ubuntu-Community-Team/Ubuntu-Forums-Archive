---
title: "Mdadm HELP!"
date: 2010-01-09
forum: Hardware
---

### Post by DarwinLabs on 2010-01-09
I am having issues with my raid 5 setup. I have created a raid 5 setup on a old machine before using 3 250GB drives and it worked great using this command

mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sda1 /dev/sdb1 /dev/sdc1

reboot the machine and all drives were apart of the md0 and everything worked great. so I created a new machine and I wanted to use 3 1TB drives so I proceeded as normal fdisk them to raid full partition. rebooted to make sure they got applied double checked setting stayed and ran the mdadm command above. except I get only roughly 1TB using 2 drives instead of the 3, so I let it create and it treats one of the drives as a spare so I let it continue thinking it would be okay but its not. When I reboot the box md0 doesn't show up and one of the drives is part of md_d0 so I have to stop it using mdadm --stop /dev/md_d0 and then reassemble the md0 with all 3 drives everytime. why is this happening can someone please help me. I also tried the --metadata=1.2 and the problem keeps happening.

---


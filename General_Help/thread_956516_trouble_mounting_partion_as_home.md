---
title: "trouble mounting partion as /home"
date: 2008-10-23
forum: General Help
---

### Post by EvilRobotDrew on 2008-10-23
first off, i am following this tutorial ([http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)), i have made a new partition, and copied everything i need over, but i cannot get this new partion to mount to /home. i have added the following line to Fstab, can someone tell me what is wrong with it?

/dev/hda3 /home ext3 nodev,nosuid 0 2

i have tried putting tabs instead of spaces, tried using tabs and spaces to line up each element of this line with the other lines in fstab, and nothing seems to work.

---

### Post by Nepherte on 2008-10-23
What error do you receive when it tries to mount? Tabs or more than one space is not necessary.

Does /dev/hda3 exist?

---

### Post by EvilRobotDrew on 2008-10-23
i wasn't getting an error, Ubuntu was creating a new home folder for me when i logged in. 

hda3 was wrong, i thought that i had made sure of the path, but i guess i didn't

---

### Post by Nepherte on 2008-10-23
/dev/hdx entries may vary, that's why it is recommended to use UUIDs instead.

---


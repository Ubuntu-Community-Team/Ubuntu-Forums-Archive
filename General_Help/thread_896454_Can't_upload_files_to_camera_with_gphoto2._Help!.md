---
title: "Can't upload files to camera with gphoto2. Help!"
date: 2008-08-21
forum: General Help
---

### Post by yesint on 2008-08-21
Dear All,
I want to upgrade a firmware of my camera. For this I have to put few files to the memory card. I don't have a cardreader, so I decided to upload them directly by USB using gphoto2.
Everything seems to go fine. The camera is recognised perfectly and I can download photos easily. The status reported by gphoto2 shows that the camera supports file uploads. So, I tried to upload files:

gphoto2 -u ./something --folder /store_00010001/DCIM/100CANON/

It works fine and after upload I can see that file in the card by doing

gphoto2 --list-files

Great, I unplugged the camera and... the uploaded file disappears! When I plug it back and do  --list-files there is no such file there!
I did a bit of research and found that *any* changes made by gphoto2 (new or deleted directories, uploaded files) disappear when camera is unplugged.
The card is write-enabled, formatting it in the camera does not help.

Any ideas?

---


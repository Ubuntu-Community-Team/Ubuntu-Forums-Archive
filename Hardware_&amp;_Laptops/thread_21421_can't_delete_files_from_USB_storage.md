---
title: "can't delete files from USB storage"
date: 2005-03-22
forum: Hardware &amp; Laptops
---

### Post by Elmo on 2005-03-22
hi there,
i have got a problem with my USB pen drive. It mounts fine, i can open it and look at the contents. I can also copy files onto it. I can also delete the files again - only problem is when i delete the files the space on the disk does not seem to increase it keeps on saying that there is only 348 kb left - however after deleting some files there should be at least 60 MB free space. in nautilus and in the console the files i have deleted are gone ... and now i can't copy anything onto it anymore because it says it doesn't have enough space ... anybody got an idea what went wrong. 
Thank you very much.

-----------------------------------

update:

i have sorted the problem ... when deleting stuff the usb drive creates a .Trash_Username folder in which it stores the deleted files --> removed the files using the Console ... everything fine now.

---

### Post by lao_V on 2005-04-08
Thanks for posting your solution! Hopefully someone will benefit from it

---

### Post by jeremy on 2005-04-08
If you enable 'Enable delete command' in Nautilus preferences (behavior), you can then delete with a right-click.
Be careful though!

---

### Post by nad on 2005-04-08
This is because the files were not deleted, just moved to the /trash directory. The previous delete method works because it bypasses the trash can and actually deletes your files!

Dan M

---


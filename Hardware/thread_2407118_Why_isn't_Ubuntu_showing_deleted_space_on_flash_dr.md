---
title: "Why isn't Ubuntu showing deleted space on flash drives"
date: 2018-11-30
forum: Hardware
---

### Post by jacatone on 2018-11-30
I've tried deleting files on numerous flash drives, but Ubuntu doesn't show the new free space. Just shows what was there before. Why is that?

---

### Post by coffeecat on 2018-11-30
Probably because you soft deleted them and they are still physically there in the hidden trash folder. However, you don't give enough information to give a definitive answer.

How did you delete the files?
Which version and flavour of Ubuntu are you running?
If you plug one of the affected flash drives in, what does the desktop trash folder show?
Plug one of the affected flash drives in and open a file browser to show the contents of the flash drive. Now show hidden files however that is done with whatever DE you may be using - usually the key combination ctrl-h will toggle view hidden files on or off. Now that hidden files are shown, is there a .Trash-1000 folder? (If you UID is not 1000, it will show a different number.) Explore that folder. Are your deleted files in a sub-folder of .Trash-1000?

Basic tip - if you want to delete files and you are 100% sure you wil not need to recover them, use the hard delete key shortcut, shift-del. Then they will be properly deleted and space will be freed up on the device/partition.

---

### Post by jacatone on 2018-11-30
Yeah, I had to do a format using a Windows machine since i couldn't get Ubuntu to do it. It did show the Trash-1000 folder. Now I can't get files to finish downloading to the flash drives. I think I'll just go back to Windows, linux is too difficult to get stuff done.

---

### Post by coffeecat on 2018-11-30
> **jacatone said:**
>  I think I'll just go back to Windows, linux is too difficult to get stuff done.

You didn't bother to answer my questions so I'll make some assumptions.

It sounds as though you soft deleted with the delete key only. You know what? **Windows does exactly the same.** -

Delete key only = soft delete = space not freed up.
Delete key + shift = hard delete = space freed up.

So if you find that too difficult, you'll find Windows too difficult as well.

---


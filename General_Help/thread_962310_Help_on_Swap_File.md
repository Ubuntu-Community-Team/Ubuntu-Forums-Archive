---
title: "Help on Swap File"
date: 2008-10-29
forum: General Help
---

### Post by Paris Heng on 2008-10-29
What exactly the swap file are? .swp? I create a script file using vim and it have created a another file namely swap file. Can somebody tell me what actually is this file? What is the function of this file?

Attached images link:

[IMG]http://img516.imageshack.us/img516/7128/problemsef2.png[/IMG]

---

### Post by ajmorris on 2008-10-29
hi there,
these .swp files created by vim are created when you edit a file. It is *normally* the same as the file that you are editing with vim at the time. It is used to keep track of the changes you have made to the file, you can use commands such as :recover to recover your file etc. The screenshot you posted, is what is shown by vim when it has already edited the file before, and the swap file already exists. You can use this system in ssh systems for example, if multiple people edit the same file, to make sure you dont try to save the file at the same time as someone else... You can only take advantage of this system though, if you delete the .swp file after editing.

AJ

---

### Post by Paris Heng on 2008-10-29
So, you mean, I can delete the swap file in any circumstances? After I delete the .swap file, will it affect the main saved file?

---

### Post by ajmorris on 2008-10-29
no, after you delete the .swp file, you can no longer recover the file, back to what it was before you have made the changes. Deleting the .swp file will have no effect what so ever on the *proper* file.


AJ

---

### Post by Paris Heng on 2008-10-29
So, the swap  file is for recovery solely? The command :recover will recover to the original file? Thanks for the info.

---


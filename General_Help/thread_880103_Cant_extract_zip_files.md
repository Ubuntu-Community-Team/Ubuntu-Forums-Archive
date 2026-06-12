---
title: "Cant extract zip files"
date: 2008-08-04
forum: General Help
---

### Post by Jdm111 on 2008-08-04
When i try to extract a 3.5gb zip file i end up a folder of about 500kb! Please help!

---

### Post by Ataris on 2008-08-04
What is the folder supposed to contain?

And do you get any errors when extracting it? Try using the terminal to see what output you get - I don't know the command for extracting zip folders because I don't normally need them.

---

### Post by Jdm111 on 2008-08-04
> **Ataris said:**
> What is the folder supposed to contain?

And do you get any errors when extracting it? Try using the terminal to see what output you get - I don't know the command for extracting zip folders because I don't normally need them.

  error:  invalid compressed data to inflate

it works in windows.

---

### Post by Ataris on 2008-08-04
Just because it works in Windows doesn't mean it will work in Linux. If you can extract it in Windows, then what do you need it for in Linux. What IS it?

Try using another archive manager or re-download it (thought that might not work). It seems that the Linux archivers don't like the format it's in. You might be out of luck.

---

### Post by Jdm111 on 2008-08-04
> **Ataris said:**
> Just because it works in Windows doesn't mean it will work in Linux. If you can extract it in Windows, then what do you need it for in Linux. What IS it?

Try using another archive manager or re-download it (thought that might not work). It seems that the Linux archivers don't like the format it's in. You might be out of luck.
Im going to using winrar in wine now to try to extract. Hopefully it will work.

---

### Post by Jdm111 on 2008-08-04
SOLVED i uses winrar in wine!

---

### Post by GhostAir89 on 2008-08-05
you don't need wine to install rar that's a rar progam which can be compilled in ubuntu.:lolflag:

---

### Post by Jdm111 on 2008-08-05
> **GhostAir89 said:**
> you don't need wine to install rar that's a rar progam which can be compilled in ubuntu.:lolflag:

Its command line based and winrar is graphical

---

### Post by Ataris on 2008-08-05
7-zip is better than Winrar, and free too, and runs well on Wine. I've noticed it can open oddly saved or corrupted archives as well. Chances are using unrar in Linux might not work either.

---

### Post by hefty on 2009-07-14
For people who might be reading this trying to find a solution to the same problem:

I had the same message "error:  invalid compressed data to inflate" when using unzip. I managed to extract the file by right-clicking on it in the file browser and opening it with "Archive Manager". I then had to select the enormous (3.5GB) file and click extract and choose a location.

---

### Post by fukuro on 2010-01-14
I was having the same problem, got the error
  "error: invalid compressed data to inflate"
when using unzip to open up a big zip file.  I stumbled upon this thread and eventually it led me to the solution.

My solution was to use 7-Zip, like someone else suggested. For example,
  7z x big_file.zip

That was it! :D

---


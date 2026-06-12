---
title: "Where is the ISO image in Ubuntu 8.04.2?"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by linmakana on 2009-06-30
I want to burn it to a CD but I cannot find the ISO image talked about in: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Please help? Thank you.

Edit: Here is my Ubuntu 8.04.2 Folder if that helps any...

[IMG]http://img37.imageshack.us/img37/9408/ubuntufolder.png[/IMG]

---

### Post by lotster on 2009-06-30
I think what you have there is the content that should go into an ISO image.  My guess is that you already have the .ISO file, and that you extracted the contents of that folder from the .ISO, by double-clicking on it?  Many archive software packages (such as 7-zip) support extracting data from ISO's as if they're zip files, so I recommend doing a search for ubuntu-8.04.2-desktop-i386.iso.

However, if your search doesn't find anything, I recommend creating an ISO with the contents of that folder using something like "Magic ISO Maker" of "folder2iso" (Google for it).  Then you can burn the .ISO file to a disc; alternatively, it MIGHT work if you just burn the contents of the folder to a disc as it is, using something like Nero (with the possible exception of booting capabilities, I'm not sure about that).

---

### Post by mcduck on 2009-06-30
> **lotster said:**
> 
However, if your search doesn't find anything, I recommend creating an ISO with the contents of that folder using something like "Magic ISO Maker" of "folder2iso" (Google for it).  Then you can burn the .ISO file to a disc; alternatively, it MIGHT work if you just burn the contents of the folder to a disc as it is, using something like Nero (with the possible exception of booting capabilities, I'm not sure about that).

Neither of these solutions would work. The image must be a bootable image, and not the kind of bootable most CD buring apps tend to do (simply adding bootable DOS system to the image).

But you are correct about the original poster most likely having simply extracted the actual .iso image, since the screenshot shows it's contents..

I can only but recommend setting Windows Explorer to show file extensions. Solves quite many problems when you *really* know what type your files are.. ;)

---


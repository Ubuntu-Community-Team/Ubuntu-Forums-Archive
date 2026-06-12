---
title: "Portable HDD size added to internal HDD size?"
date: 2008-07-11
forum: Hardware
---

### Post by Nubsy on 2008-07-11
Sorry, if this doesn't go here, but I figured it was a hardware thing. (feel free to move this if necessary) 

First off, I'm using Ubuntu Hardy. So I have a little portable hard drive, a "Cutie pocket hard drive disk". It's 40GB, and formated comes to 37.3GB. The internal HDD, which is 30GB, formats to 26.3GB. So far so good. I plugged in the portable HDD, because my music is on it, and I wanted some music on my Ubuntu box. I was going to move the files to the internal hard drive, but after I decided it would be a better idea to just keep the porta-drive attached. So I deleted the music I copied over, emptied the trash and whatnot. So I went to the disk usage analyzer to see if it was gone, and it gave me a weird reading.

It's telling me that my total filesize is **63.6GB** When I know it's not. It tells me I've used 18.3GB, which I know I haven't. And tells me I have 45.3GB free. Which I dont. However, all of these numbers DO make sense if you add together the sizes of the Internal HDD (where linux is installed) and the porta-drive where my music is. (26.3 + 37.3 = 63.6, 12.3 used (internal) + 6.0 used (porta) = 18.3, etc.)

Is there a reason why it's adding them together? Because they are not the same drive. 

Also, when I unmount the portable drive, it goes back to what it should be for the internal drive. When this happens, it tells me I have 14GB free, but Nautilus says it's only 12.7GB free. Any ideas.

Thank you for your time. :)

---

### Post by Nubsy on 2008-07-11
bump...

---

### Post by medo_87 on 2008-08-01
Hi Nubsy,

I have just came along your post. When you check the file system size in the disk usage analyser it adds all the available data storage space in the system as all drives go under the same heirarichy/Filesystem under linux. 
That's what I believe anyway.

Hope it is correct

---


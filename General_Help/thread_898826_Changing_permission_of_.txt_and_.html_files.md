---
title: "Changing permission of .txt and .html files"
date: 2008-08-23
forum: General Help
---

### Post by Elcid247 on 2008-08-23
i have many .txt files and .html files on my NTFS partitions. im really annoyed by the dialog box tht keeps poping everytime i want to open any file.

i tried opening nautilus as root and changing the permission from the properties, the permission gets unchecked, but it gets checked again right after 1 second....lol!

i also tried *"chmod -x <filename>"* and *"chmod a-x <filename>"* with root privilages but no luck either.

and whenever i try changing the owner from root to my user, it keeps insisting tht the owner is the root!


o and also, those .html files r actually a website tht we designed for a college project, it works pretty smooth on xp using same FireFox version, but in ubuntu, .gif images don't show and all the links keep giving me "could not find the requested file" error... does tht have anything to do with execution permissions?

---

### Post by LateNiteTV on 2008-08-23
well "chmod -x" removes execution privs. "chmod +x" adds execution privs. what do you want to be able to do to the files? just read them? u could do like... "chmod 0664 *files*"

---

### Post by Elcid247 on 2008-08-23
thnx but still no luck :(

yes i wana be able to read .txt files directly when i open them without dealing with the execution dialog box

and as for .html, im suspicious tht the privilages r the problem behind the .gif image not showing and links not working,,, so am i right about tht? otherwise wht could it be? this is my 3rd installation of ubuntu and i have had the same issue everytime

---

### Post by LateNiteTV on 2008-08-23
wait a sec, youre trying to read files from ntfs on ubuntu?

---

### Post by Elcid247 on 2008-08-23
> **LateNiteTV said:**
> wait a sec, youre trying to read files from ntfs on ubuntu?


yep... is tht wrong? everything works just fine except for these 2 issues..


do i have to change the whole layout of my partitions and make them something like FAT32 so theyd be readable on both? or do i have to have the files on ext3 in order to have proper privilage control?


i am about to format my whole HD to fix my parition layout anyway... so any recomendations would be nice

---

### Post by Silent Ninja on 2008-08-23
You can set them to "just read" on the Folder Preferences

---

### Post by Elcid247 on 2008-08-23
> **Silent Ninja said:**
> You can set them to "just read" on the Folder Preferences

where is tht?

---

### Post by snova on 2008-08-23
I think I know what is happening.

NTFS is not the problem. NTFS doesn't work really well under Linux because it's hard to get specifications- so nobody knows much about how it works. But we can at least read from them.

I think your problem is that you somehow changed ownership of these files to root. Because of this, you are no longer permitted to open them. Only a file's owner (or root, because he can do anything) can change the owner. So open Nautilus as root, and change the owner of all these files to your user.

After this, never open Nautilus as root again unless you're sure you have to.

Now, as far as permissions go, your files need to be readable at least. Linux files have three kinds of permissions: To read a file, to write to the file, and to execute it. YOU should have the first two for normal files and all three for programs. Nobody else should be able to write to them- give other people only read permissions.

Directories are a little different- the same permissions apply, but they have different effects. Read means the permission to view the contents of a directory. Write permissions mean you can create and delete files within it. Execute permissions are what let you enter a directory. So follow the same advice for files when setting directory permissions- but add the execute permission to them.

Your problems with GIF's have nothing to do with either NFTS or permissions. GIF is like NTFS- we can't do much with them because of patents. We are legally prevented from doing certain things with GIF files, notably compression. It's patented.

Try converting them to another format. GIF is not the best. PNG works with every browser I've ever used, and they are compressed as well as or better than GIF.

---

### Post by Elcid247 on 2008-08-23
actually i did try changing the owner to my_user through root nautilus, but when i select my_user, it changes to my_user and then back to root after less than 1 sec..

thnx for the png idea, i had to search a while till i realized it was .apng, but still this doesnt fix the links issue..

---


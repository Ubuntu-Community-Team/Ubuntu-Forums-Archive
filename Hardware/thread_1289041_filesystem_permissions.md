---
title: "filesystem permissions"
date: 2009-10-12
forum: Hardware
---

### Post by billyboy1995 on 2009-10-12
can i make the main filesystem's permissions so that anyone can read and write on it without screwing up ubuntu? I know how to use the command line or GUI things so don't be afraid to give me a resonce that you think i will not under stand.
 
Thanks in advanced Bill

---

### Post by hal10000 on 2009-10-12
If i had read/write permission to your /, you could not prevent me from erasing your /usr or /lib or any other directory or file.

It's a very bad idea to change the default permissios on files or directories you did'nt create yourself, you would surely mess up your whole system if you don't know **exactly** what you are doing.

[EDIT]
you could use extended arrtibutes (chattr and lsattr commands) to set a file or directory e.g. with the immutable flag (see man chattr for more info), but you would have to adjust thousands of files in your system, and i'm not sure if this would make much sense.

---

### Post by billyboy1995 on 2009-10-12
but i have it set up as a share drive and i would like to be able to write to it from the other computer. is there any way for me to do that without messing it up? or is it still going to be the same?

---

### Post by hal10000 on 2009-10-13
I have to administrate about 90 computers, and i always login via [COLOR="Red"]ssh[/COLOR] if i have to do something on a remote computer. With [COLOR="Red"]ssh -X[/COLOR] you can even run X-Windows programs. With ssh you can use the remote computer as if you were on your local machine, including sudo commands.

---

### Post by billyboy1995 on 2009-10-13
thats not what im looking for. i don't want a remote desktop app i want to be able to write info on to my filesystem drive directly from windows xp.

---

### Post by hal10000 on 2009-10-14
I suspected that it's not what you are looking for, but i can't imagine a reason why you want to do this. You would not write to /usr or /lib when you are on the local machine, because these are not the places where simple "info" would reside, and there must be very very strange circumstances why you want to do it from a remote computer.

I know some people who tried to give write permissions to their whole system, you can do this with 
[COLOR="Red"]sudo chmod -R o+w /[/COLOR], but believe me or not, they all ended up in reinstalling their system.

---

### Post by scorp123 on 2009-10-14
> **billyboy1995 said:**
> i want to be able to write info on to my filesystem drive directly from windows xp. There is no business in being able to do that. You should only ever write into your own /home directory. Messing with system-wide file permissions will break the system.

And why "from Windows XP"? Can you please explain more? Are you using the Linux system as SAMBA server? Or how are you accessing the filesystem from Windows XP?

If you want users to be able to exchange data with each other then there are better ways ... e.g. give them a group share (e.g. "/home/shared") which has permissions set in such a way so that each member of a certain user group (e.g. "sambausers" ?) can read and write into that folder.

Locations outside of /home simply should never ever be touched. You're just going to ruin your system.

---

### Post by billyboy1995 on 2009-10-14
well all i really want to do is be able to write to my home directory not anything else. i don't know if i can put home as the only share or if i have to put the whole filesystem to a share. The only reason i am on xp is because my family computer has gone down so they have mine and i am borrowing my dads netbook so like i said i want to be able to write to my home diretory so i don't have to send everything to myself or have to flashdrive or anyother way of moveing files. Sorry if i wasn't as detailed as i needed to be but i am still new to the whole fourm thing.. never had to write them when i used xp but since moveing to ubuntu i have been needing a lot of help.

---

### Post by hal10000 on 2009-10-14
Now i understand.
You should install and start the samba server on the ubuntu machine and then in your file-manager right-click on your /home/username folder and enable filesharing via samba

This should be enough.

---

### Post by billyboy1995 on 2009-10-19
Thanks alot it worked.

Bill

---


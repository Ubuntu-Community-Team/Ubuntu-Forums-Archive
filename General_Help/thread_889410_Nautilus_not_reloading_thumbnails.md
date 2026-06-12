---
title: "Nautilus not reloading thumbnails"
date: 2008-08-14
forum: General Help
---

### Post by tencent on 2008-08-14
Im not sure if this problem was caused by something on my part or if its just an error with Nautilus itself but here it goes. With my camera whenever you delete images off the card the counter starts over on the file names. The problem here is that I started having completely different photos using the same thumbnail totally confusing me until I realized it was just the thumbnails that where messing up. Anyways to make a quick easy solution to fix this problem you can follow the following steps.

From a terminal
sudo touch /usr/bin/destroythumbnails
sudo gedit /usr/bin/destroythumbnails

When gedit opens copy and paste this line
rm -f ~/.thumbnails/normal/*

close the editor and you should be back to a prompt in your terminal.
sudo chmod a+x

That last command should make our new command available for execution by all users without giving them permission to edit the code of the command which follows the security scheme Ubuntu already uses, I believe at least.

Finally test that it works by opening up nautilus under your user account and navigating to 
~/.thumbnails/normal/

Once in the directory you will likely see a ton of thumbnails. So back to your terminal type this.
destroythumbnails 

Now look back at the directory you are viewing in nautilus and you should see that all the images have been deleted.

Now this last part is optional but this is what works best for me.
Open System>Preferences>Sessions

Click Add and enter a name of your choosing and then obviously destroythumbnails as the command. This will clear out any generated thumbnails on startup. Theres several other things you could do such as setting the command to run whenever you plug in a usb device, ie your camera or making the command run on a cron tab etc so thanks to Linux's flexibility you should be able to do whatever fits you best. What i did was just quick and easy so I hope it helps someone that doesn't have much experience or knowledge to fix this problem themselves.

Maybe someone should submit this as a feature idea? Seems to me the thumbnail generation should have a check to prevent this from happening naturally without having to delete the thumbnail directory.

---

### Post by kstella on 2009-07-26
Thanks, I was having the same problem.

Just curious, what model is your camera? I didn't have this problem with other cameras.

---

### Post by kstella on 2009-07-26
Oh, hey. It turns out that I didn't have to go into the command line; I just had to find .thumbnails in my home folder and delete it.

Here's the thread: [http://ubuntuforums.org/showthread.php?t=633524](http://ubuntuforums.org/showthread.php?t=633524)

---


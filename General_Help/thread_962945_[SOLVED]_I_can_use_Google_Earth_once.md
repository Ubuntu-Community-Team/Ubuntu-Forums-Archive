---
title: "[SOLVED] I can use Google Earth once"
date: 2008-10-29
forum: General Help
---

### Post by Handssolow on 2008-10-29
I've a problem with Google Earth. After an apparently successful install of 4.3 on my 8.10 Beta Intrepid, I select to start using the program which I can. However, if I close and re-open the program the Earth has disappeared as have the options in the lower left hand box.

Is it a root permission problem or something else?

---

### Post by sefs on 2008-10-29
I can remember there was a problem during installing where the final screen asks you to launch google earth...if you do that then you are in trouble because you are launching it as the root user or a user with sudo privs.  When it reaches that final screen you just close and exit and then launch from the desktop or menu item.


It was discussed on the forums when 8.04 came out, so if you do a search you may find the thread.

---

### Post by Handssolow on 2008-10-29
I noticed the thread you are refering to sefs and had earlier tried a re-installed without selecting start at the end but it made no difference. I also tried altering the permissions of the desktop configuration file using gksudo nautilus but it made no difference, I couldn't restart Google Earth a second time without the Earth being missing.

I suspect it's something simple, if I only knew what it was.

---

### Post by Handssolow on 2008-10-30
It does seem to be a root permission issue with my install of Google Earth.
In the terminal "sudo googleearth" launches the full program whereas just using "googleearth" doesn't, neither goes clicking Applications>Internet>Google Earth, the program starts but Earth has disappeared.

Which part or file do I need to alter the permissions of?

---

### Post by Handssolow on 2008-10-30
Problem solved after I found this-
[http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/](http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/)

Quoting from alop

Here’s how to fix the “only works with sudo” problem
in your homedir, cd .config/Google, then do ’sudo chown [your user name] GoogleEarthPlus.conf’

Next time you run googleearth, it’ll show you an error message about not being able to write to /root/.googleearth, and that it will use your homedir instead…

If you read this alop, many thanks from Handssolow.

---


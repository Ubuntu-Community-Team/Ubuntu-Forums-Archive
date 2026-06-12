---
title: "[SOLVED] Automatically move files that land on the desktop to another folder"
date: 2008-08-31
forum: General Help
---

### Post by Arcnsparc on 2008-08-31
I am using hardy and would like to set it up so any file that gets saved to the desktop is moved to another folder in my home directory.  I am trying to stay clean :P  Thanks!

---

### Post by drs305 on 2008-08-31
> **Arcnsparc said:**
> I am trying to stay clean :P  Thanks!

For a truly 'clean' desktop, turn it off. It will always be clean. 

```
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop 'false'

```
Change the value to 'true' to restore...

Of course, I realize this isn't what you were asking for ...

---

### Post by Arcnsparc on 2008-09-07
If I do that my conky wont work, but thanks!  I guess Ill just have to be over-meticulous about keeping things tidy :S

---

### Post by ryanhaigh on 2008-09-07
Save this script to a file in your home directory, make it executable and add it to your session startup applications making changes to username and the destination directory.

```

#!/bin/bash
while [ 1 ];do
    #for each file on the desktop
        for file in /home/username/Desktop/*; do
        #move the file to another folder
        mv $file /home/username/otherfolder
    done
    #wait 2 minutes and check again
    sleep 120
done

```

---

### Post by Arcnsparc on 2008-09-07
Shoot son that is perfect! I dont know why I didnt think of that!  Thanks.

---

### Post by x-g on 2008-09-07
> **Arcnsparc said:**
> If I do that my conky wont work, but thanks!  I guess Ill just have to be over-meticulous about keeping things tidy :S

Conky works with icons turned off.  That's the way I have my desktop set up.

---

### Post by anjilslaire on 2008-09-07
Also, change the default download location in Firefox to something other than your Desktop...

---

### Post by kostkon on 2008-09-07
If you mean the files you download with *Firefox* (if that's the browser of your choice), then why not use the very useful [*Download Sort*]("https://addons.mozilla.org/en-US/firefox/addon/25") extension?

---

### Post by anjilslaire on 2008-09-08
well, Firefox is the default browser in most cases, and the OP didn't detail where most of their files originate from, so I just threw teh Firefox comment in to help.

If a user creates a file otherwise, why put it on th Desktop in the 1st place if they don't want it there? I don't like stuff on mine, so I just don't ever put things there in the 1st place.

Also, its usually easier to make a settings adjustment in Firefox for most inexperienced users than to install an extra extension & then configure that.

But, to each his own :)

---

### Post by Arcnsparc on 2008-09-08
Thanks all!  Between changing firefox default download and making a script to sort out which files go where I think this thread is sufficiently solved!

---


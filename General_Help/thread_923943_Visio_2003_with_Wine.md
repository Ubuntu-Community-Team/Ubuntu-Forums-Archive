---
title: "Visio 2003 with Wine"
date: 2008-09-18
forum: General Help
---

### Post by joesmoe10 on 2008-09-18
Hey, I'm using Ubuntu 8.10, trying to get Visio 2003 to run under wine 1.0   When I load it up it hangs at the splash screen with the error

"IOPL not enabled"

Other people had success enabling the gdiplus library with winecfg , but no such luck for me.  I know there are open source diagramming tools like dia, but my class is using visio and none of the free apps will open .vsd files.  Any ideas?

Thanks,
Joe

---

### Post by Meow27 on 2008-09-18
dont mean to look cold but, did you check appdb?
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2727](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2727)

some1 marked it gold there under hardy, you might want to check it out

---

### Post by joesmoe10 on 2008-09-21
I did find appdb, I was just hoping that there was a better way than reinstalling it.  

I got it work using winetricks.  Even though I enabled gdiplus in the library view, I didn't have it installed.  With the winetricks I installed  gdiplus and it worked.  Of course now visio is complaining that its not installed for the current user.

---

### Post by najeer on 2008-11-08
Folks this worked for me on November 8, 2008


You must have de WINEPREFIX set to run nicelly wine.
2 ways to do it:

Edit /etc/enviroment and add at the end of file the:
Quote:
WINEPREFIX="/home/~/.wine"

Or set it itch time you run wine with:

Quote:

WINEPREFIX="/home/~/.wine" wine winfile.exe
Note that winfile.exe is the file that you are running on wine.

Hope helps.

eschuch.blogspot.com

---

### Post by imaginateca on 2009-09-29
Same problem here, but solved:

When configure Wine, you have to tell some libraries to be native, bultin. That is ok for all them EXCEPT gdiplus, which has to be only native (click edit button and select native -only native-), NOT bultin. Then it runs with no problem.

Cheers.

---


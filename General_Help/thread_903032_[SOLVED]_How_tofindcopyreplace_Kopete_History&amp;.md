---
title: "[SOLVED] How to:find/copy/replace Kopete History&amp;amp;Firefox Bookmarks?"
date: 2008-08-27
forum: General Help
---

### Post by HousieMousie2 on 2008-08-27
Hi, I have two issues here that are similar in nature... wanting to replace new data with old data, namely Kopete and Firefox...

I got a larger hard drive, so instead of upgrading my Gutsy (on a 17GB HDD) I installed a fresh Hardy (on a brand new 320GB HDD.)

Now I am wanting to fetch my Kopete chat History (from Linux HDD) and Firefox Bookmarks (from Win XP HDD.)

ISSUE #1:
I haven't even been able to locate the place where the History is saved at, much less figure our how to append the old chat History to the new one.

Any ideas?


ISSUE #2:
Firefox's Import does not see the Windows Bookmarks (of course.)  I found the /etc/firefox/profile/bookmarks.html and tried to replace it with the bookmarks.html from Gutsy.  Silly me, since it says it is an auto-generated html and not to edit it, but does not say where/what generates it.  I would prefer the ones from Windows instead of the old ones from Gutsy.  

Anyone know how to replace the current (Linux) bookmarks with the desired (Windows Firefox) bookmarks?



Cheers and thanks for taking the time!

---

### Post by ThrobbingBrain66 on 2008-08-27
> **HousieMousie2 said:**
> Hi, I have two issues here that are similar in nature... wanting to replace new data with old data, namely Kopete and Firefox...

I got a larger hard drive, so instead of upgrading my Gutsy (on a 17GB HDD) I installed a fresh Hardy (on a brand new 320GB HDD.)

Now I am wanting to fetch my Kopete chat History (from Linux HDD) and Firefox Bookmarks (from Win XP HDD.)

ISSUE #1:
I haven't even been able to locate the place where the History is saved at, much less figure our how to append the old chat History to the new one.

Any ideas?

ISSUE #2:
Firefox's Import does not see the Windows Bookmarks (of course.)  I found the /etc/firefox/profile/bookmarks.html and tried to replace it with the bookmarks.html from Gutsy.  Silly me, since it says it is an auto-generated html and not to edit it, but does not say where/what generates it.  I would prefer the ones from Windows instead of the old ones from Gutsy.  

Anyone know how to replace the current (Linux) bookmarks with the desired (Windows Firefox) bookmarks?



Cheers and thanks for taking the time!

Bookmarks:
Exporting the bookmarks from XP as an html file and then importing them into your Ubuntu Firefox will work, I've done this many times.

Kopete:
Your chat logs are probably kept in kopete's settings folder in your /home directory (the folder name is probably .kopete).  Hit Ctrl+H to show these hidden folders.

---

### Post by HousieMousie2 on 2008-08-27
> **ThrobbingBrain66 said:**
> Bookmarks:
Exporting the bookmarks from XP as an html file and then importing them into your Ubuntu Firefox will work, I've done this many times.

Kopete:
Your chat logs are probably kept in kopete's settings folder in your /home directory (the folder name is probably .kopete).  Hit Ctrl+H to show these hidden folders.

Thanks for the Kopete suggestion... it was a little more obscured than just .Kopete, but I found it none the less.  Oh and it is Alt+., not Ctrl+H, at least in Kubuntu Hardy it is.

Found them at:

/home/.kde/share/apps/kopete/logs/(and in my case...)YahooProtocol/<my account name>

Just copied and pasted... presto.

As for the Export/Import, my question becomes how?  When I asked Firefox to Import, it INSTANTLY returned "No programs that contain bookmarks, history or password data could be found." and did not give any other options aside from Close.


Thanks for the post and taking the time... any more info?

---

### Post by Ms_Angel_D on 2008-08-27
if your running firefox on both systems install the [foxmarks]("http://www.foxmarks.com/") extension to both it will sync your bookmarks between computers.

---

### Post by HousieMousie2 on 2008-08-27
> **MetalHellsAngel said:**
> if your running firefox on both systems install the [foxmarks]("http://www.foxmarks.com/") extension to both it will sync your bookmarks between computers.

That looks like it will work for me (hopefully.)  I am still kind of wanting to find out how to just move them without involving another application, or website, but if all else fails... it is certainly doable.  

Thank you!

Just to be clear, it isn't two computers, just multiple hard drives in the same computer.

((I would like to know how to do it manually that way I am not limited to just Firefox bookmarks.))

Cheers!


EDIT:

AHAH!  In this instance the Import that is in the File menu is useless, however, the Import that is in the Bookmarks menu.../Organize Bookmarks/Import and Backup, is just what I needed, it let me navigate to the html file.

Thank you both again for your prompt posts and assistance!

---

### Post by Ms_Angel_D on 2008-08-28
If your using firefox 3 you can open the bookmark manager

Bookmarks >> Organize Bookmarks

there is an import and backup feature right there. It will give you the option to backup either in .json format or html.

Also  you may want to check out the [FEBE]("https://addons.mozilla.org/en-US/firefox/addon/2109") extension for firefox it will backup all your firefox settings. (extension, bookmarks, preferences, and themes). I use it quite frequently. Hope this is a bit more helpful.

---


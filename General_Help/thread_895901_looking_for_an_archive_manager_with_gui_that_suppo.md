---
title: "looking for an archive manager with gui that supports..."
date: 2008-08-20
forum: General Help
---

### Post by linuxed on 2008-08-20
I'm trying to find an archive manager for linux that resembles the windows version of 7-zip as closely as possible.  I'm constantly using archives that contain other archives.  For example, a zip file that contains another zip file.  The only reason I use the 7-zip program is that when I double click an archive inside of another archive it will automatically open in the same window.  I can then modify any of those files and save them.  Then when I close the 7-zip window I'm prompted whether I want to update the original archive.

I've tried using ark, file-roller and karchiver.  Unfortunately none of those programs provide the interface that I'm accustomed to.  The file-roller application comes the closest, but it still opens the files in a new window and it also prompts me to update both archives each time I modify a file and click save.

Is there any linux archive application with a gui that allows you to open archives within archives in the same window?  And only prompts you to update the original archive when the window is closed?

---

### Post by mb_webguy on 2008-08-20
Well, if the interface is really that important to you, why don't you just install 7-zip using Wine?

---

### Post by Shippou on 2008-08-20
I think the person just like a native application, not one in wine.

Well, mb_webguy has a point though: you can install pkzip-7 if that interface is really important to you.

Or.. ;) if you are really good at programming, make one and post it here and at sourceforge.net. :)

Just a thought. :)

Good luck for your hunting! :)

---

### Post by linuxed on 2008-08-20
@mb_webguy
I used Wine once in the past.  After installing it I installed a simple windows program as a test.  The window program failed to work so I attempted to uninstall it.  Halfway through the uninstall process it reported an error and I realized that the entire OS was ****ed.  Something to do with missing modules.  After logging out I was never able to get Ubuntu to load after that so I doubt I'll ever try Wine again.

It's not so much the overall look/feel of the interface that I care about, just 2 specific features.  Being able to navigate the archive through the gui by double clicking files, folders and other archives  and having folders and archives open in the same window.  I'd also prefer to not be prompted to update both archives when I save a file.  If I'm working on a file that's in an archive within another archive, when I click save I only want the archive that I'm working in to be updated.  Then when I close the window I want to receive a prompt to update the original archive.

The only reason I'm interested in having those features is to simplify the process of updating nested archives (archives contained in another archive).  Otherwise there's quite a few additional steps involved in trying to edit a file located in a nested archive.

I just tried peazip and q7z which didn't provide the functionality I was looking for either.  Any other suggestions?

---

### Post by mb_webguy on 2008-08-20
While I certainly understand the feeling of reluctance to return to a application that burned you, what version of Wine did you previously install?  I've installed the version available from the Wine HQ website several times without any problems at all.  In fact, I have 7-zip, Internet Explorer (using IEs4Linux), and MS Office 2003 installed right now...

While I certainly haven't used them all, I really can't think of any archiver for Linux that has the features you mention.  I use File Roller except when I want to use the ultra compression settings for 7z.  It works well enough for me, and on the occasion I need to modify nested archives it doesn't bother me to have separate windows.  

As I said, while I understand your reluctance to try Wine again, if you want those features of 7-zip, installing 7-zip with Wine is probably your best bet.  Just make sure if you decide to do so that you get the version from the Wine HQ website by adding their repository.

---


---
title: "Cannot find new GDM Themes (Screens)"
date: 2008-08-08
forum: General Help
---

### Post by ragflan on 2008-08-08
Hi. I'm under Hardy Heron. I want to install a new GDM theme for the Login Window. So I navigate to Login Window under Administration menu. Then I click the add button to add a new GDM theme right? I did this before. Lots of times. But now when I want to add a new theme, I cannot find them.

I've attached 2 screenshots. I have to enter the root password to change the Login Window, right? Once I do that, and the Login Window opens up and I press the add button, I cannot find the GDM themes to install. 

In both the screenshots, you can see that there are 2 themes on my desktop. Okay, one of them is definitely a GDM theme, and the other needs to be repackaged as *.tar.gz, but the thing is. I cannot see them from the 'Add' window under Login Window menu.

The screenshot differences:

First one is showing an empty Desktop under my username.
Second one is showing an empty Desktop under root. 

Did I mess something up? I know I did this before without any problems.

[CENTER][IMG]http://ramipage.googlepages.com/Screenshot.resized.png[/IMG]

[CENTER][IMG]http://ramipage.googlepages.com/Screenshot-1.resized.png[/IMG]

---

### Post by mcduck on 2008-08-08
Those themes are not packaged correctly. They should be in .tar.gz packages..

You could simply extract the, and then compress them again, this time into the right format. After that they should work.

By the way, you should resize your screenshots before posting them to forums..

---

### Post by ragflan on 2008-08-08
Sorry about the screenshots. I did that. I even have a copy of the old themes that I installed onto the GDM Login Window menu. They worked back then. But now I cannot even see them. 

I kept a copy of all the Themes I downloaded. It doesn't work. I cannot see the files.. Does it have anything to do with root? I can add themes easily to change Metacity themes. But I'm having a problem with Login Window themes.

---

### Post by nazish on 2008-08-08
Login manager supports themes only in the tar.gz format. You first unpack them onto your desktop and then again pack them in the tar.gz format. This will solve your problem.

---

### Post by ragflan on 2008-08-08
Yes, I know that much. It's obvious that certain files are packaged for Login Window, and certain ones for Metacity and so on. I understand that. I also unpacked and repacked them with the same format as they originally were: *.tar.gz. 

But I cannot even locate those files on my directories, yet I can still see them on the Desktop.

Here's the thing. I know for sure, that I added custom GDM themes before. I kept all those files in a folder within my Home drive. But now, I cannot view them either when I try to add the themes to GDM. But they're right there in the folder, but when I navigate through the Add function in Login Window, they're not there.

Did I screw up somewhere with privileges or.. something? Any clues?

---

### Post by mcduck on 2008-08-09
Well, the permisssions could be the problem if their permissions are set so that they aren't readable by others. Because the GDM setups runs as root,  so if your  own user owns the files and other users aren't allowed to read them the GDM setups wouldn't be able to access the files.

---

### Post by ragflan on 2008-08-09
How do I check if this is the case? And if it is the case of permissions, how do I set them correctly?

---

### Post by mcduck on 2008-08-09
Since the packages are on your desktop, and owned by your own user, all you need to do is right-click them, select Properties and on the Permissions-tab make sure that "Others" have at least read access to them.

---

### Post by ragflan on 2008-08-10
Is it supposed to be like this? (I didn't change anything now or ever in this menu.)

[IMG]http://ramipage.googlepages.com/Screenshot-DesktopProperties.png[/IMG]

---

### Post by mcduck on 2008-08-10
I suppose those are the permissions for the Desktop directory? That seems to be OK. But You should check the permissions of the theme packages as well..

---

### Post by ragflan on 2008-08-10
Yeap, that's the permissions for my desktop. The odd thing is (when I click the ADD button and the window pops up for me to browse for the file), in the 'browse-for-file' window, I cannot see the theme packages which are actually there in the folder I navigate to. 

But if I drag the theme files from my folders into that browse window (which is still at the same folder where it originally cannot see the theme files), I can suddenly see all the packages in that folder. Is this odd behaviour? Or if not.. did I mess something up?

---

### Post by ragflan on 2008-08-10
> **mcduck said:**
> I suppose those are the permissions for the Desktop directory? That seems to be OK. But You should check the permissions of the theme packages as well..

[IMG]http://ramipage.googlepages.com/ok1_screen.png[/IMG]

The above is a screenshot of permissions for the Login Window theme package file (*.tar.gz GDM theme). Does it look right?

---

### Post by mcduck on 2008-08-10
Sure, the permissions seem to be correct. I also doenloaded that "Relaxing - Open Solaris" GDM theme you have, extracted it and then compressed it into .tar.gz and I had no problems installing it..

I have no idea why it doesn't work for you. But if nothing else works, then you can just install it manually. Press Alt-F2 and run "gksudo nautilus" to open the file manager as root, and then use that to extract the theme directory into /usr/share/gdm/themes.

---

### Post by ragflan on 2008-08-11
Hey thanks a lot man. You've been really helpful explaining things to me. I can still drag the themes into the 'Add Theme' dialog and then it magically can see all the theme files in that folder (which just a second ago it wouldn't see anything). I just have to drag the themes from a folder into that 'Add Theme' dialog and it works fine.

It's not a problem, just an inconvenience and I wanted some answers to know what was causing this behaviour. You've helped me understand permissions and I thank you for that.

---


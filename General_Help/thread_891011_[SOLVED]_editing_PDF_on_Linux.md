---
title: "[SOLVED] editing PDF on Linux"
date: 2008-08-15
forum: General Help
---

### Post by kelpie_canada on 2008-08-15
I was sent an application by email to fill out and return. Unfortunately it was in PDF format. How do I convert this to allow me to fill it in as Open Office?

---

### Post by unutbu on 2008-08-15
Adobe's Acroread has the ability to fill in forms (and print) -- though I think the free version does not allow you to save the modified pdf.

---

### Post by mb_webguy on 2008-08-15
> **unutbu said:**
> Adobe's Acroread has the ability to fill in forms (and print) -- though I think the free version does not allow you to save the modified pdf.
Ditto unutbu.  You can install Acrobat by adding the [Medibuntu repositories]("https://help.ubuntu.com/community/Medibuntu").

There's also PdfEdit ("sudo apt-get install pdfedit" in the terminal to install), but it's pretty low-level and not terribly user-friendly for the casual user.

---

### Post by kelpie_canada on 2008-08-15
I tried to install Acroread and got this error message

/tmp/AdobeReader_enu-8.1.2_SU1-1.i486-1.rpm could not be opened, because the associated helper application does not exist. Change the association in your preferences.

I have no idea what this means or what to do to fix it.

---

### Post by mike2357 on 2008-08-15
I was able to install Acrobat Reader successfully by going to [http://www.adobe.com]("http://www..adobe.com"), clicking on "Get Adobe Reader", then "Different Language or operating system".  Then in the drop-down box labeled "Select an Installer", choose the .deb option.

After downloading the file, double-click on it and select "Install Package".

---

### Post by mb_webguy on 2008-08-15
> **kelpie_canada said:**
> I tried to install Acroread and got this error message

/tmp/AdobeReader_enu-8.1.2_SU1-1.i486-1.rpm could not be opened, because the associated helper application does not exist. Change the association in your preferences.

I have no idea what this means or what to do to fix it.

Why are you trying to install a rpm instead of the version from the Medibuntu repository?  Rpm packages aren't designed for Debian Linux (on which Ubuntu is based).  The deb (as in Debian) package from the Adobe website would be better, but installing it from the Medibuntu repository is the easiest and best, since you use Synaptic (or apt-get) to install it (and therefore uninstall it if you want to).

---

### Post by kelpie_canada on 2008-08-15
> **mike2357 said:**
> I was able to install Acrobat Reader successfully by going to [http://www.adobe.com]("http://www..adobe.com"), clicking on "Get Adobe Reader", then "Different Language or operating system".  Then in the drop-down box labeled "Select an Installer", choose the .deb option.

After downloading the file, double-click on it and select "Install Package".

I followed your instructions precisely and got the following error message again

/tmp/AdobeReader_enu-8.1.2_SU1-1.i386.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.

Now what do I try?

---

### Post by kelpie_canada on 2008-08-15
> **mb_webguy said:**
> Why are you trying to install a rpm instead of the version from the Medibuntu repository?  Rpm packages aren't designed for Debian Linux (on which Ubuntu is based).  The deb (as in Debian) package from the Adobe website would be better, but installing it from the Medibuntu repository is the easiest and best, since you use Synaptic (or apt-get) to install it (and therefore uninstall it if you want to).

I am sorry but I have only had this system since May and am still trying to figure out how things work. It is my first system because I didn't want to line Gates's pockets any more then they already have been.

I don't know what you are referring to. I went to the Medibuntu repository and followed the directions and it didn't work. I have never attempted to go to the terminal.

---

### Post by mb_webguy on 2008-08-15
Seriously.  Follow the instructions on [this page]("https://help.ubuntu.com/community/Medibuntu") to add the Medibuntu repository, then either type "sudo apt-get install acroread" or install it with Synaptic.

---

### Post by minhaaj on 2008-08-15
Well its not a permanent solution but you might want to use online services like zamzar.com to convert it into a document file and then convert back in pdf, through openoffice or zamzar, but i use acrobat reader on my ubuntu hardy and its running fine. Didnt try filling out forms though so no idea.

---

### Post by kelpie_canada on 2008-08-16
I want to thank those of you who tried to help me with this problem. 

I took minhaaj's advice and went to zamzar.com and it worked perfectly. When I have had my system a little longer and feel more confident and comfortable with it I will try going to the terminal and follow mb-webguy's advice about installing Acroread in my system.

I am a novice on computers but I know more today than I did when I bought it and I will know more next week, next month then I do today.

Katie

---


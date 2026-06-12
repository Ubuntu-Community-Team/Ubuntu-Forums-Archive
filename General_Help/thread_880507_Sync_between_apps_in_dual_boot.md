---
title: "Sync between apps in dual boot"
date: 2008-08-05
forum: General Help
---

### Post by h0bbe on 2008-08-05
I'm planning a dual boot on my computer at work (I really can't get rid of Windows there). Is it possible to sync data between apps used on both systems (Ubuntu and Windows) locally, like Firefox bookmarks and Evolution calendar and contacts etc?

---

### Post by hyper_ch on 2008-08-05
for firefox you can use the same profile.

But what do you want to sync evolution calendar/contacts with? What do you use on windows? The only way I see would be to sync evolution with egroupware (or another software like it) and have both (evolution and outlook) to sync with it.

---

### Post by h0bbe on 2008-08-05
> **hyper_ch said:**
> for firefox you can use the same profile. I guess I have to save the profile on a shared disk and set up both Firefox to look at the same profile?

I just realized that I also have the option to use Foxmarks. I already do that to sync between different computers.

> **hyper_ch said:**
> But what do you want too sync evolution calendar/contacts with? What do you use on windows? The only way I see would be to sync evolution with egroupware (or another software like it) and have both (evolution and outlook) to sync with it. My plan is to use Evolution on both Ubuntu and Windows. I'm not keen on syncing via Google and would rather do it locally on the hard drive just by letting Evolution read the same files on both systems if possible. I'll have a look at eGroupWare.

---

### Post by hyper_ch on 2008-08-05
> **h0bbe said:**
> I guess I have to save the profile on a shared disk and set up both Firefox to look at the same profile?
Linux can read/write to ntfs and windows can read/write to ext2/3.
So no need for a real shared disk.

> **h0bbe said:**
> My plan is to use Evolution on both Ubuntu and Windows.
Evolution is available on Windows?

---

### Post by h0bbe on 2008-08-05
> **hyper_ch said:**
> Linux can read/write to ntfs and windows can read/write to ext2/3.
So no need for a real shared disk.
But how do I make Firefox use the same profile both in Ubuntu and Windows? Is there a setting somewhere to point to the same folder?

**EDIT:** I found a Howto: [http://ubuntuforums.org/showthread.php?t=203524&highlight=share+firefox+profile+ubuntu+windows](http://ubuntuforums.org/showthread.php?t=203524&highlight=share+firefox+profile+ubuntu+windows)

> **hyper_ch said:**
> Evolution is available on Windows?
[http://www.softpedia.com/get/Internet/E-mail/E-mail-Clients/Evolution-for-Windows.shtml](http://www.softpedia.com/get/Internet/E-mail/E-mail-Clients/Evolution-for-Windows.shtml)

---

### Post by hyper_ch on 2008-08-05
In windows you have the profile.ini in c:\Documents and Settings\USER\Application Data\Mozilla\Firefox

the profile.ini contains the path to the profile that shall be used.

So you could alter that path by (1) installing ext2/3 drivers and then (2) mount the linux partition as drive and assign the path to /home/USER/firefox/.....

Or in linux you could mount the ntfs disk in the local filesystem somewhere (e.g. /media/c_drive) and then chang the profile.ini in linux to point to the path there (e.g. media/c_drive/Documents and Settings/.....)

For evolution you should also have a profile folder that you can make both use them same - I think... never tried evolution on windows so I don't know for sure.

---

### Post by H4rm0ny on 2008-08-05
> **h0bbe said:**
> But how do I make Firefox use the same profile both in Ubuntu and Windows? Is there a setting somewhere to point to the same folder?


Although Linux can read/write to NTFS, I would recommend putting the mozilla directories on a shared disk anyway, for security and portability and minimal hassle. Up to you though. I use a USB disc for this sort of stuff when needed.

Regardless of where you place this, the way you would set this up in Linux is to find the .mozilla/firefox directory in your home directory, and edit the profiles.ini file to point at where you want to store your profile directory. It's just a text file and self-explanatory. Just alter the Path parameter and change IsRelative to 0 if you want the path name to start from "/" rather than the current location.

For Windows, the process is the same, but your profiles.ini file will be found in (from memory) the "Local Settings/Applications/Mozilla" directory in your user profile. Root around, you'll find it.

If you have an existing profile you want to keep, whether from Windows or Linux, just copy that entire profile directory to the new shared location. Firefox and Thunderbird both handle having their profiles moved around extremely well. :)

Does this help?

-H.

---

### Post by h0bbe on 2008-08-05
Maybe [this]("http://ubuntuforums.org/showthread.php?t=554741") will solve it for Evolution. I'm a newbie but will Evolution really handle a link as a folder? I guess I'll have to try it.

---


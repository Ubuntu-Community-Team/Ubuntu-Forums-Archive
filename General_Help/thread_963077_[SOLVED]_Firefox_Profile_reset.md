---
title: "[SOLVED] Firefox Profile reset"
date: 2008-10-29
forum: General Help
---

### Post by Buschbarber on 2008-10-29
I have Ultimate 1.9 and suddenly, today, Firefox launches and the Homepage is Blank. There are no Bookmarks.

I checked the Edit/Preferences menu and the default Homepage is still chrome://ubufox/content/startpage.html, but when I click on the Homepage icon, the Google Search address bar appears, instead.

I looked in the Default Profile and there is a Bookmark.html file that is about 80k in size. It contains a number of earlier Bookmarks. There is a Bookmarks Backup folder with Bookmark files ending with the extension .json, from 10/24-10/29, and are about 198k in size, but I do not know how to Restore them.

The thing is, if the existing, smaller, Default Bookmark.html file is not being read, it would appear that Firefox is not working properly.

How can I correct this and not loose anything?

It seems like the Cookies are working as I can go to Gmail or Ubuntu Forums and I am still logged on automatically.

---

### Post by lovinglinux on 2008-10-29
Backing up the entire profile folder is not a bad idea before trying to restore your bookmarks.

To restore bookmarks, open Menu >> Bookmarks >>> Organize Bookmarks >>> Import and Backup >>> Restore then select the date or browse the json file you want to restore.

After restoring, you could use [FEBE extension]("https://addons.mozilla.org/en-US/firefox/addon/2109") to create regular backups of your entire profile or just some settings. In case something goes wrong like now, you can restore the entire profile with just a few clicks.

---

### Post by Buschbarber on 2008-10-30
I tried Bookmarks/Organize Bookmarks/Restore, but when I choose the date I want to Restore, it says "Unable to Process Request"

---

### Post by lovinglinux on 2008-10-30
> **Buschbarber said:**
> I tried Bookmarks/Organize Bookmarks/Restore, but when I choose the date I want to Restore, it says "Unable to Process Request"

Try browsing the json file instead of choosing the date.

---

### Post by Buschbarber on 2008-10-30
By Browsing, do you mean Right-Click on the json file, choose Open With, and choose Firefox?

I have found that although there is a Bookmarks.html in my Profile, it is only 80k, as opposed to the json files which are much larger. The Bookmarks.html will display when I Open With Firefox, but the json files will not.

I checked Edit/Preferences and my Default Homepage is still specified, but when I click on the Homepage icon, I only get the Google Search addressbar.

I tried removing the Localstore.rdf, but that did not do anything.

I could only find one profile.

---

### Post by Buschbarber on 2008-10-30
I loaded a page and tried to Save a Bookmark. When I clicked on Bookmark this Page, no Dialog Box came up to name it and it did not Save anything.

---

### Post by lovinglinux on 2008-10-30
> **Buschbarber said:**
> By Browsing, do you mean Right-Click on the json file, choose Open With, and choose Firefox?

No. Go to Bookmarks administration and try to restore a backup, but instead of using the available dates, browse the json file you mentioned before.

If this doesn't work, you could delete the file places.sqlite from your profile (back it up first) and then try to restore the json file.

> **Buschbarber said:**
> I have found that although there is a Bookmarks.html in my Profile, it is only 80k, as opposed to the json files which are much larger. The Bookmarks.html will display when I Open With Firefox, but the json files will not.

I guess you have a bigger problem. The json files are compressed files, but they should be displayed as text when opening with Firefox as you did. What I would do in a situation like this is install FEBE extension and back everything, but not as a single profile. FEBE has an option to backup settings, extensions and other stuff individually. Then create a new profile in Firefox, check if it works properly then try to restore ythe settings, extensions and so on, one by one using FEBE. Please notice that to restore settings with FEBE you should not be using the profile you want to restore the settings to. This means that you will perform the backup and the restore using your current profile. After finishing restoring, then you can open your new profile and the settings, bookmarks and extensions should be there.

> **Buschbarber said:**
> I checked Edit/Preferences and my Default Homepage is still specified, but when I click on the Homepage icon, I only get the Google Search addressbar.

I tried removing the Localstore.rdf, but that did not do anything.

I could only find one profile.

Try again after deleting places.sqlite

> **Buschbarber said:**
> I loaded a page and tried to Save a Bookmark. When I clicked on Bookmark this Page, no Dialog Box came up to name it and it did not Save anything.

I think you have a corrupted "places.sqlite" file. This is the file that stores bookmarks and related stuff. I had a similar problem a while ago and deleting this file solved the problem.

---

### Post by Buschbarber on 2008-10-30
Deleting the places.sqlite did the trick. I was able to Restore the Bookmarks and everthing else seems to be working normally.

The problem started about the time I was trying to get Google Earth to work. Both 4.2 and 4.3 will not load and give me an error stating that my video card is Unknown.

Could the install of Google Earth have affected the files in my Firefox profile?

What do you think of Foxmarks? My IT buddy tells me it works great for syncronizing and backing up Bookmarks.

---

### Post by lovinglinux on 2008-10-30
> **Buschbarber said:**
> Deleting the places.sqlite did the trick. I was able to Restore the Bookmarks and everthing else seems to be working normally.

Good to know. Please don't forget to set the thread as SOLVED, so other people willing to help does not waste time reading this and other people looking for a solution to the same problem can easily find it. You can do this with the "Thread Tools" menu above the posts. 

> **Buschbarber said:**
> Could the install of Google Earth have affected the files in my Firefox profile?

I don't think so.

> **Buschbarber said:**
> What do you think of Foxmarks? My IT buddy tells me it works great for syncronizing and backing up Bookmarks.

Yes, it works great.

---

### Post by Buschbarber on 2008-10-30
Thanks again!!

---


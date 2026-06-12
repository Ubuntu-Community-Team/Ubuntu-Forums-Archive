---
title: "How do i change ubuntu 8.04 theme"
date: 2008-08-07
forum: General Help
---

### Post by Millie da kidd on 2008-08-07
Well i don't know how to download a theme.
I want to download this theme [http://www.gnome-look.org/content/sh...?content=86716](http://www.gnome-look.org/content/sh...?content=86716)

Thank you in advance

---

### Post by rudihawk on 2008-08-07
Hi, once you have downloaded a theme. YOu can go to Preferences->Appearance and drag the folder into the theme tab, it should install it for you and then you can select it, and make use of it.

---

### Post by Millie da kidd on 2008-08-07
> **rudihawk said:**
> Hi, once you have downloaded a theme. YOu can go to Preferences->Appearance and drag the folder into the theme tab, it should install it for you and then you can select it, and make use of it.

Doesnt work what i get is a circle with a line across is when i try to drag it in.:confused::confused:

---

### Post by sayakb on 2008-08-07
Alternatively, extract it and you'll get a folder. Now open your Home Folder, press Ctrl+H to show hidden folders, open the .themes folder and paste the extracted folder in it. Now goto System->Preferences->Appearance and select the theme. If it does not appear in the list, press Customize button, click the Controls tab and select it from there.

---

### Post by Millie da kidd on 2008-08-07
> **LinuxIsInnovation said:**
> Alternatively, extract it and you'll get a folder. Now open your Home Folder, press Ctrl+H to show hidden folders, open the .themes folder and paste the extracted folder in it. Now goto System->Preferences->Appearance and select the theme. If it does not appear in the list, press Customize button, click the Controls tab and select it from there.

I can't find the theme folder when i click home folders.
all i see is
desktop, music, pictures, examples, documents, video, public, and templates.
Or do i have to make it?

---

### Post by sayakb on 2008-08-07
As I mentioned, Press Ctrl+H to reveal them.

---

### Post by Millie da kidd on 2008-08-07
> **LinuxIsInnovation said:**
> Alternatively, extract it and you'll get a folder. Now open your Home Folder, press Ctrl+H to show hidden folders, open the .themes folder and paste the extracted folder in it. Now goto System->Preferences->Appearance and select the theme. If it does not appear in the list, press Customize button, click the Controls tab and select it from there.

I did everything you said to do here and nothing.

---

### Post by steveneddy on 2008-08-07
> **Millie da kidd said:**
> I did everything you said to do here and nothing.

You aren't paying attention.

The folder is called

**[COLOR="Red"].themes[/COLOR]**

see the dot before the file name?

**[COLOR="Blue"]That means it is a hidden file.[/COLOR]**

Open your /home folder and hit

**[COLOR="Blue"]ctrl+h[/COLOR]** and it will show you hidden files.

You have to scroll down too see them.

K?

Now drop the theme you downloaded into the .themes folder.

If it is the correct file type you will be able to choose it as a theme.

Alternately:

Right click the desktop, 

select "Change Desktop Background"

on top select the "Theme" tab

on the bottom is a button that says "Install" on it

Click the "Install" button and browse for the theme file you just downloaded and if it is the correct file type it will install it for you and ask you if you would like to use this theme now? Yes or no

K?

Hope this helps.

EDIT:

You may click the Thanks button if you wish. Just trying to get over 100 Thanks.

---

### Post by Millie da kidd on 2008-08-07
> **steveneddy said:**
> You aren't paying attention.

The folder is called

**[COLOR="Red"].themes[/COLOR]**

see the dot before the file name?

**[COLOR="Blue"]That means it is a hidden file.[/COLOR]**

Open your /home folder and hit

**[COLOR="Blue"]ctrl+h[/COLOR]** and it will show you hidden files.

You have to scroll down too see them.

K?

Now drop the theme you downloaded into the .themes folder.

If it is the correct file type you will be able to choose it as a theme.

Alternately:

Right click the desktop, 

select "Change Desktop Background"

on top select the "Theme" tab

on the bottom is a button that says "Install" on it

Click the "Install" button and browse for the theme file you just downloaded and if it is the correct file type it will install it for you and ask you if you would like to use this theme now? Yes or no

K?

Hope this helps.

EDIT:

You may click the Thanks button if you wish. Just trying to get over 100 Thanks.
I did everything you told me and it doesnt appear as a theme.

---

### Post by steveneddy on 2008-08-07
> **Millie da kidd said:**
> I did everything you told me and it doesnt appear as a theme.

Your link is bad from the first post.

Repost the link to the gnome-look page sowe can look at what you are trying to install as a theme.

Themes are not GTK, only GDM.

GTK is for a login theme, not a theme for the desktop.

EDIT:

I will allow you to thank me again.

:D

---

### Post by rainwalker on 2008-08-07
Just FYI, some themes don't show up in the main window, you have to click the "Customize" button and select the parts (controls, window border, icons) manually.

---

### Post by DaymItzJack on 2008-08-08
> **steveneddy said:**
> Your link is bad from the first post.

Repost the link to the gnome-look page sowe can look at what you are trying to install as a theme.

Themes are not GTK, only GDM.

GTK is for a login theme, not a theme for the desktop.

EDIT:

I will allow you to thank me again.

:D

You are confusing the two, is that why he should thank you? GDM is the login theme.

Looking at his url, the content option is '86716', which is a Emerald theme. 

Install emerald (type in terminal): ```
sudo apt-get install emerald
```

Then go to System->Preferences->Emerald Theme Manager, from there click the button that says "Import..." and find your theme.

---

### Post by Millie da kidd on 2008-08-08
> **DaymItzJack said:**
> You are confusing the two, is that why he should thank you? GDM is the login theme.

Looking at his url, the content option is '86716', which is a Emerald theme. 

Install emerald (type in terminal): ```
sudo apt-get install emerald
```

Then go to System->Preferences->Emerald Theme Manager, from there click the button that says "Import..." and find your theme.


yea iv installed emerald compiz fusion i have a couple themes an when i click them nothing happends

---

### Post by halln on 2008-08-08
The file that you downloaded from Gnomelook.org should at least under GTK2 that's the theme files and if you want the window border (EMERALD) It should be under beryl. Now if you sure you downloaded a theme file, Go to apperance/install theme/file location(if you saved the downloaded file into your desktop)click desktop as file location/choose the file/open. It should install your theme now, then click customize, search for your theme (drop down menu) and apply. Hope this helps, I,m standing by.

---

### Post by Millie da kidd on 2008-08-08
> **halln said:**
> The file that you downloaded from Gnomelook.org should at least under GTK2 that's the theme files and if you want the window border (EMERALD) It should be under beryl. Now if you sure you downloaded a theme file, Go to apperance/install theme/file location(if you saved the downloaded file into your desktop)click desktop as file location/choose the file/open. It should install your theme now, then click customize, search for your theme (drop down menu) and apply. Hope this helps, I,m standing by.

But how come i cant set any of the ones i have installed already on emerald:confused::confused:

---

### Post by sayakb on 2008-08-09
Ok.. you can install a GDM theme (theme for the Ubuntu login window) by going to System->Administration->Login Window, press Local tab and press Add.

To install a GTK theme, drop the theme on the System->Preferences->Appearance window and it should say that The theme has been successfully installed. Then find it in the list, or press customize and the Controls and Window Borders tabs to select it from the list.

If it is an emerald theme, then first, press **Alt+F2** and type in:
```
emerald --replace
```
(This should give you an emerald window border if you have emerald installed)
Now open emerald (System->Preferences->Emerald theme manager), press Import button and add the .emerald theme (if the one you have downloaded is a tar.gz file, extract it first) and it should appear in the list. Clicking on the theme should apply it.

Now.. what is the file format? Extract it and tell us the file's contents. Plus, does the theme appear in the Emerald theme manager list, or it doesn't?
Here is the Moomex theme: [http://www.gnome-look.org/content/show.php/Moomex-Theme?content=57063](http://www.gnome-look.org/content/show.php/Moomex-Theme?content=57063)
This has a GTK and an emerald theme. Try out both.

---


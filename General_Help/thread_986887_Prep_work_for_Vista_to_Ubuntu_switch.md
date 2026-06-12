---
title: "Prep work for Vista to Ubuntu switch?"
date: 2008-11-19
forum: General Help
---

### Post by Gizim on 2008-11-19
So im trying to prep to switch from Vista into Ubuntu wondering what would be the best way to go about the switch. I have alot of videos and music as well as pictures i need to keep. But i want to make sure that there aren't any permission issues when i make the switch. Ive always found after the the switch i can access the files but all other accounts have issues any suggestions?

---

### Post by deadowl on 2008-11-19
Well, there are different types of preparation.

1. You can install OpenOffice, Pidgin, Firefox, and the GIMP on Windows to adjust yourself to the applications you'll be using. Evolution, Rhythmbox, and Totem meanwhile, do not have Windows versions (afaik). You can still use Thunderbird and VLC on both platforms in place of the latter.

2. Just back up your photos/audio/video/documents. It would be best to have a separate category for each.

3. What you can do for permissions:

There are three levels of permission:
User   - owner of the file
Group  - owner's group: you shouldn't have to worry about this concept
Others - everyone else

There are three types of permission:
Read    - can open the file
Write   - can save the file
Execute - can run the file as an application

If you want to give everyone the ability to view all of your files:
-Select all of your files
-Right-click -> Properties
-Permissions Tab
-User/Group/Others -> Read only or Read/Write, whichever you prefer.

---

### Post by Gizim on 2008-11-19
> **deadowl said:**
> Well, there are different types of preparation.

1. You can install OpenOffice, Pidgin, Firefox, and the GIMP on Windows to adjust yourself to the applications you'll be using. Evolution, Rhythmbox, and Totem meanwhile, do not have Windows versions (afaik). You can still use Thunderbird and VLC on both platforms in place of the latter.

2. Just back up your photos/audio/video/documents. It would be best to have a separate category for each.

3. What you can do for permissions:

There are three levels of permission:
User   - owner of the file
Group  - owner's group: you shouldn't have to worry about this concept
Others - everyone else

There are three types of permission:
Read    - can open the file
Write   - can save the file
Execute - can run the file as an application

If you want to give everyone the ability to view all of your files:
-Select all of your files
-Right-click -> Properties
-Permissions Tab
-User/Group/Others -> Read only or Read/Write, whichever you prefer.

If they are files from when i had Windows installed who would be the default owner? Root? or my account?

---

### Post by tgalati4 on 2008-11-19
Back up your important media before you repartition your drive.  Generally when you shrink a Windows partition down and install Ubuntu, the Windows drive just shows up (as it does on the Live CD).  It is read-only to prevent destroying any Windows data.

You need to mount it with root access to be able to write to the Windows drive in Ubuntu.

You don't make a clear distinction if this is a dual-boot system or an Ubuntu-only system.  The preparation for each case may be different.  For instance, you will need to cover your ears for the loud applause for the second case.

---

### Post by Gizim on 2008-11-19
> **tgalati4 said:**
> Back up your important media before you repartition your drive.  Generally when you shrink a Windows partition down and install Ubuntu, the Windows drive just shows up (as it does on the Live CD).  It is read-only to prevent destroying any Windows data.

You need to mount it with root access to be able to write to the Windows drive in Ubuntu.

You don't make a clear distinction if this is a dual-boot system or an Ubuntu-only system.  The preparation for each case may be different.  For instance, you will need to cover your ears for the loud applause for the second case.

Sorry yes this will be a clean wipe and fresh Ubuntu :)

---

### Post by TeXtonyx on 2008-11-19
> **Gizim said:**
> So im trying to prep to switch from Vista into Ubuntu wondering what would be the best way to go about the switch. I have alot of videos and music as well as pictures i need to keep. But i want to make sure that there aren't any permission issues when i make the switch. Ive always found after the the switch i can access the files but all other accounts have issues any suggestions?

You might try dual booting with Vista and Ubuntu for awhile. Maybe you will
find programs that work just as well with the same functionality on Ubuntu 
as you have with Vista. I also like Firefox and Thunderbird, but Evolution
might be more like Outlook. It depends if you have any new programs that
won't run on Wine or they also use a program named VirtualBox. I'm not sure
that Linux has any program as good as Adobe Acrobat Pro Writer. I'm justa
saying maybe your transition should be a bit more gradual, if you have any
eclectic video editing software on Windows see if there is a sub first.
There are Linxu/Vista dual boot tutorials or Howtos available with pics :-)

---

### Post by Marcus Derekus on 2008-11-19
Or do a wubi install. It comes ubuntu cd and allows you to install ubuntu as an application on windows (no partitioning required). Then you can dual boot between the two OS's . For more info go to [http://wubi.sourceforge.net](http://wubi.sourceforge.net)

---

### Post by Gizim on 2008-11-19
> **TeXtonyx said:**
> You might try dual booting with Vista and Ubuntu for awhile. Maybe you will
find programs that work just as well with the same functionality on Ubuntu 
as you have with Vista. I also like Firefox and Thunderbird, but Evolution
might be more like Outlook. It depends if you have any new programs that
won't run on Wine or they also use a program named VirtualBox. I'm not sure
that Linux has any program as good as Adobe Acrobat Pro Writer. I'm justa
saying maybe your transition should be a bit more gradual, if you have any
eclectic video editing software on Windows see if there is a sub first.
There are Linxu/Vista dual boot tutorials or Howtos available with pics :-)

Well i've made the switch many times so im not new i guess its just the small things such as permissions and access User/Groups ect.. the on going Logitech G7 thumb button not working issues that get me ;)

---

### Post by tgalati4 on 2008-11-19
If you are trying to divide up photo albums from Windows to different users in Ubuntu, then that will cause a problem.  There is a migration assistant, but I have not used it, so I don't know how well it works.

You might try dividing the media up within Windows first.  Backup that media for each user.  Wipe the disk clean and do a fresh Ubuntu install.  I hear clapping in the background.  Then create separate user accounts and have each user copy their media back to home folders.  That way permissions are assigned correctly.  It's tedious, but that's the only way I know how to do it.

If one user simply copies all the media over, then that user has permission and the other users are locked out.  This sounds like your situation.  As far as the Logitech mouse, I assume that you sent an email to Logitech asking them why they have not provided Linux support.

Good luck. And congratulations on taking back your computer.  Don't forget to share your experiences in the testimonial section of the forums.  There are many more right behind you.

---

### Post by Gizim on 2008-11-19
> **tgalati4 said:**
> If you are trying to divide up photo albums from Windows to different users in Ubuntu, then that will cause a problem.  There is a migration assistant, but I have not used it, so I don't know how well it works.

You might try dividing the media up within Windows first.  Backup that media for each user.  Wipe the disk clean and do a fresh Ubuntu install.  I hear clapping in the background.  Then create separate user accounts and have each user copy their media back to home folders.  That way permissions are assigned correctly.  It's tedious, but that's the only way I know how to do it.

If one user simply copies all the media over, then that user has permission and the other users are locked out.  This sounds like your situation.  As far as the Logitech mouse, I assume that you sent an email to Logitech asking them why they have not provided Linux support.

Good luck. And congratulations on taking back your computer.  Don't forget to share your experiences in the testimonial section of the forums.  There are many more right behind you.

Is there a way i can copy all the videos/pictures/music to "neutral" area within Ubuntu so that anybody can access it? only really me and one other person will be using the system any way.

---

### Post by tgalati4 on 2008-11-19
Create a directory:

```

>sudo mkdir /home/Shared_Video
>sudo chmod 777 /home/Shared_Video

```


Put all of your media in that directory.  The mode 777 gives read, write, and execute privilege for all users for anything put in that directory.  See:  *man chmod* for details.

If you need more restrictive permissions, you can assign a group (or groups) and give each group specific permissions.  See: *man chown* for details.

---

### Post by Marcus Derekus on 2008-11-19
If you run **gksudo nautilus** in terminal a new window will open up that allows you to access/read/write no matter what the permissions are.

plus using this window you can change permissions to ANY FILE/FOLDER YOU'D LIKE TO. 

but do be carful when changing permissions cuz you can mess up your system

---

### Post by GmAz on 2008-11-19
I went from Vista to Ubuntu 8.04, now on 8.10.  I found it was wasier to get into Ubuntu by just ditching Vista 100%.  Dont' get me wrong, I like Vista. Yes, I said it, I like it, but since I don't game anymore, I decided to toy with Ubuntu.  And you know, I like it.  Its a nice OS.

As for videos, pictures and music.  I had all my data on a seperate drive, NTFS formatted and I had no issues with mounting it or using the files either.  I have several types of video formats on it, all MP3 music and my pictures are a variety of JPGs, BMPs, PNGs and a few other less familiar formats.  I just select the drive from the places menu and it mounts for me.  

I do run a few apps with Wine from windows.  Mostly they are small apps for specific uses.  WinSCP for SSHing into my iPhone, that kind of specific stuff.  

After you get into Ubuntu, you'll notice that you will be missing a few things that you are used to in Windows, but give it a week or two and you will easily adapt to the way stuff is done in Linux.

Simply put, I would say get your data on a seperate hard drive or flash drive then wipe your drive and put Ubuntu on it only, and hide the Vista CD.  If you feel tempted to ditch Ubuntu for Windows again, resist.  Ubuntu really is fun and for most people, it is very functional and has tons of of features as well as TONS of free open-source apps available at your finger tips.

Oh, don't forget about these forums.  If you run into a problem, don't hesitate to ask.  I've asked some really stupid questions and gotten very good advice and help.

---


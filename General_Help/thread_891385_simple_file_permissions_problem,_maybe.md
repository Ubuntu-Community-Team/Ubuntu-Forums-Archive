---
title: "simple file permissions problem, maybe"
date: 2008-08-16
forum: General Help
---

### Post by fooey on 2008-08-16
let's say i created a directory /tempshare
& i gave group: "test" FULL access to tempshare

group "test" consists of 2 users
user1 & user2

each user can create a file in tempshare, but they cannot edit what each other has created.

chown root:test tempshare
i have done the chmod 770 tempshare


at first i found out it was b/c of the default umask
so i changed the umask in /etc/login.defs to 002 
(just in case i did the same in .bash_profile for both user1 & user2 (umask 002))

i'm still running into the problem to where when the user1 or user2 creates a file,  they cannot edit each others files they created.

i just get perms denied. :confused: what am i missing?

---

### Post by Phases on 2008-08-16
I'm having this very problem. (Asked fooey for help, he posted here).

What he said is the problem I'm having. I've been asked why in the world I'd want to do this, so let me explain. If there is a better way to do it, I'm open for suggestions. 

I created a folder on my newly installed Ubuntu computer. I created it in the root, called it share.

/share

I want my wife and my account both to be able to put files, mainly pictures, in there from either account and have the other account be able to modify them. 

I've done everything I can think of, and since I'm new(ish) to this that probably isn't much. 

I've made us both members of group 'home', and gave home rights. Yet, the only way I can get what I want is with 777. I do 770 and we lost it again. I guess it's treating us as "other".

Yet home has full access. I've changed our umask to 002..  

No luck.

Forgive me if I sound newbish, it would be because I kinda am. 
Thanks for any  help.

---

### Post by bingoUV on 2008-08-16
When user1 creates a file in /tempshare, see the ownership and permissions of this file. For user2 to be able to edit this file, 
1. owner should be user1, 
2. group owner should be "test", 
3. permissions should be 770

1 is true by default, and 3 will be true because you changed the umask to 002. But 2 will not be true by default, and I think there is no simple way to make it happen.

Check if what I have written above is true. If there is sufficient demand, I can write a script that will fix this. If you feel enthusiastic, install inotify-tools and use it in your script.

EDIT: And please share this script, as this is a common question here.

---

### Post by fooey on 2008-08-16
> **bingoUV said:**
> When user1 creates a file in /tempshare, see the ownership and permissions of this file. For user2 to be able to edit this file, 
1. owner should be user1, 
2. group owner should be "test", 
3. permissions should be 770

1 is true by default, and 3 will be true because you changed the umask to 002. But 2 will not be true by default, and I think there is no simple way to make it happen.

Check if what I have written above is true. If there is sufficient demand, I can write a script that will fix this. If you feel enthusiastic, install inotify-tools and use it in your script.

EDIT: And please share this script, as this is a common question here.

Thanks for the reply. All 1 & 2 are true for my situation. part 3 is not. it defaults back to the umask 022 of any file created by one of those users, which is why I'm confused & posting this. If you wouldn't mind, the script would be greatly appreciated.

---

### Post by bingoUV on 2008-08-16
Then you do not need a complicated script. Umask is being reset to 022 by some startup script that is called after /etc/login.defs. Just add the following to the end of as many startup scripts as you can think of
```

umask 002

```

e.g. /etc/profile, /etc/bash.bashrc/, ~/.bashrc for both users.

But are you sure the group owner of a newly created file is test? Have you made "test" the primary group of user1 and user2? This would make ANY file created by these users to be owned by the group "test". Try creating a file from user1 in the home directory of user1 ?

---

### Post by sisco311 on 2008-08-16
> **bingoUV said:**
> 

But are you sure the group owner of a newly created file is test? Have you made "test" the primary group of user1 and user2? This would make ANY file created by these users to be owned by the group "test". Try creating a file from user1 in the home directory of user1 ?

+1
 
OP:to set the primary group to test:
```
sudo usermod -g test  *username*
```

---

### Post by Phases on 2008-08-16
Ok. First, thanks for the replies guys. Second, I'm so confused. I'll try to explain.

It looks to me like I've done things right, but clearly I haven't.

Here are the commands I've put in, and what I get back, starting from beginning.

sudo mkdir HomeShare
ls -al

I see: drwxr-xr-x   2 root   root  4096 2008-08-16 12:25 HomeShare

sudo chown user1 HomeShare
chgrp home HomeShare
ls -al

I see: drwxr-xr-x   2 user1 home  4096 2008-08-16 12:25 HomeShare

chmod 770 HomeShare
chmod g+s HomeShare
ls -al

I see: drwxrws---   4 user1 home  4096 2008-08-16 12:33 HomeShare

sudo usermod -g home user1
sudo usermod -g home user2
umask

I see: 0002

su user2 +pass
umask

I see: 0002

I checked the above mentioned scripts, /etc/profile, /etc/bash.bashrc/, ~/.bashrc and made sure it said umask 002 at the bottom of each.

So, going back and forth between both accounts in startx, this is what I see:

Right click the HomeShare folder and go to properties, permissions:  

Owner - User1, folder access: create and delete files. file access:---
Group - home, folder access: create and delete files. file access:---
Others - Folder access: none. file access: ---

(Shouldn't it have file access as read and write, too?)

So, then I make a folder inside that folder, as user1, and it's properties/permissions look like this:

Owner - User1, folder access: create and delete files. file access:---
Group - home, folder access: access files. file access:---
Others - Folder access: access files. file access: ---

Through a: chmod -R 770 HomeShare command in desperation, no change. 
ls -al from INSIDE HomeShare, I get this

drwxrws---  4 phases home 4096 2008-08-16 13:04 .
drwxr-xr-x 23 root   root 4096 2008-08-16 12:25 ..
drwxr-sr-x  2 phases home 4096 2008-08-16 12:58 untitled folder

I don't get why its not giving the group full access, and why it's giving other some access. 

Thanks for your help.

Edit: I don't fully understand the s bit. So, if I -s HomeShare, the s changes to x, same with folders created inside, but still unusable by user2.

---

### Post by bingoUV on 2008-08-16
I don't think you need the s bit. 

The problem is that nautilus when creating your "untitled folder" does not respect your umask (002). It forces group to have no write permissions.

I just tried a similar setup like yours, and it worked with this script (filepermd.sh, which I am attaching). It ensures that permissions of any files in a given directory (its sub-directories and so on) are always 770. It also ensures that owner of files is root, and group owner is the group you specify ("home" in your case).

Steps:
1. Install inotify-tools from synaptic.
2. Store the file filepermd.sh in /usr/local/bin. You will have to do it as root.
3. Give execute permission (again as root)
4. In /etc/rc.local, before the last line that says "exit 0", add this
```

nice /usr/local/bin/filepermd.sh <full path to HomeShare directory>  home

```

As you see, it takes 2 arguments. The directory to monitor, and the group to force permissions.

You prefix it with nice so that it runs at a low priority. Anyway it is  supposed to be very efficient so hopefully you don't need the nice but keep it for safety.

By adding it to /etc/rc.local you ensure it will run every time you boot your computer. For now, before you reboot, you can just try running it as root
```

sudo nice /usr/local/bin/filepermd.sh <full path to HomeShare directory> home

```

Of course, no guarantees, express or implied ;)

EDIT: Latest version of the script can be obtained at [http://bingouv.blogspot.com/2008/08/script-to-fix-directory-permission-and.html](http://bingouv.blogspot.com/2008/08/script-to-fix-directory-permission-and.html)

---

### Post by Phases on 2008-08-16
Thanks for your help.

I was in the middle of messing with ACLs to see if I could accomplish my goal that way. However I was having some trouble. 

So, I saw your reply, and followed your instructions step by step. Everything seemed to go well. But, it didn't work.

It looks like it did in fact change the owner of HomeShare to root, did different for things created inside it. I created two folders in it, here they are:

drwxr-xr-x  2 user1 user1 4096 2008-08-16 14:12 untitled folder
drwxr-xr-x  2 user1 user1 4096 2008-08-16 14:13 untitled folder 2

---

### Post by bingoUV on 2008-08-16
You have to keep the script running. Did you stop it? Or did it stop running on its own?

EDIT: and please append the directory path by a trailing slash if you have not already done so.

---

### Post by Phases on 2008-08-16
As soon as I run the command my terminal window fills with infinite:

ls: cannot access HomeShare/untitled: No such file or directory
ls: cannot access folder: No such file or directory
ls: cannot access 3/: No such file or directory
ls: cannot access HomeShare/untitled: No such file or directory
ls: cannot access folder: No such file or directory
ls: cannot access 3/: No such file or directory
ls: cannot access HomeShare/untitled: No such file or directory
ls: cannot access folder: No such file or directory
ls: cannot access 3/: No such file or directory

and goes and goes. The first time, it crashed my computer. (When I switched to her account to create a file, it gave same thing in terminal, when to switch back and comp froze). I rebooted, tried to create a folder in HomeShare, same permissions, not 770. So I ran the command again, and my terminal is filled with it again. How can I stop it?

Edit: I thought maybe it needed the first slash, since you said full path. It's right on the root. So I changed it to /HomeShare/ 

Same result.

Edit again: Error log on crash:
Aug 16 14:45:10 Phases778 kernel: [  915.004377] inotifywait[5923]: segfault at 00000000 eip b7e26283 esp bf82fcac error 4

---

### Post by bingoUV on 2008-08-16
Get it from here: [http://bingouv.blogspot.com/2008/08/script-to-fix-directory-permission-and.html](http://bingouv.blogspot.com/2008/08/script-to-fix-directory-permission-and.html)

Initially just add it to your /etc/rc.local but don't reboot. Run it as I mentioned earlier, and check if it works for you.

---

### Post by Phases on 2008-08-16
I'm sorry man, I'm not sure what you're asking me to do. So what I did, I just ran it again:

sudo nice /usr/local/bin/filepermd.sh /HomeShare/ home

gave me a msg that indicated all was well. 

I created a folder in HomeShare, as soon as I created it my terminal filled up with all that stuff again.

But, looking at the newly created file's permissions, while my terminal is going nuts: 770.

I cntl C the terminal to stop it. Create another file, and it's not 770.

(also note, both times I ran this, when I clicked inside my 'explorer' window in startx to make the file or whatever, it closed the window, then reopened it in a different directory)

---

### Post by bingoUV on 2008-08-16
Sorry, it is a work in progress. It was created for myself long ago, but I don't have spaces in my filename so didn't work for you. My apologies.

Now I have tested it with spaces, and other weird characters in filename and saved it on the link I mentioned earlier. But it is a homebrew, and initially it will have hiccups.

I don't understand the last sentence. Reopened in a different directory? Which directory did the files move to?

---

### Post by Phases on 2008-08-16
Ok, I changed the file to what you had on your blog. 

It works! 

By the last sentence I meant, I'm in startx, I'm using explorer (i guess that's what I'll call it) to navigate the file system. 

I've been inside the HomeShare directory during the start of this, so I can make a folder and check the permissions to check my progress.

What I meant was when I clicked the window to give it focus so I could right click and say "make new folder" the window closed. Then it reopened, in a different directory other than HomeShare. 

But, bottom line, it works! I haven't tried a reboot yet, so I'll do that now. 

I appreciate your effort on this, I've been struggling with it for a couple days! Is there anything I need to do, or even just anything I CAN do, or look at, to make sure this script isn't doing anything in the background to strain my system? 

I'll reboot and test, brb.

---

### Post by Phases on 2008-08-16
(See above message)

Rebooted - it worked! You're a lifesaver. I really do appreciate your help. 

Is that blog of yours something you just came up with and you're going to try to maintain, for stuff like this? I'll bookmark it.

Edit: Also, are there any restrictions I need to keep in mind, characters in filenames, etc?

---

### Post by bingoUV on 2008-08-16
Please don't call it explorer, its developers have given it a name: nautilus. But between us, explorer is perfectly clear.

I don't know why the window will get closed, I'll try that. It generally closes when the directory is removed and recreated.

Yes, it is important that this script does not strain you system. It is designed not to strain, but it is the work of a few minutes and there are definitely defects in it. Steps you can take

1. As I mentioned, use "nice" to start it. Even if it takes CPU resources, it will never block other processes if niced.

2. Update sometimes. Sorry I don't have an apt repository so you could get automatic updates. If somebody points out a defect in the script, or I find out myself, I'll update the code on that link. You can check last modification date on the page and decide. In fact I have made a minor change just 5 minutes ago ;). Doesn't impact you, don't worry.

3. Take a look at your CPU monitor. When gone crazy, this script takes 20% of my CPU. Add the "System Monitor" applet to your gnome panel. It will take care of all misbehaving applications : firefox, nautilus, video player etc.

---

### Post by Phases on 2008-08-16
> **bingoUV said:**
> Please don't call it explorer, its developers have given it a name: nautilus. But between us, explorer is perfectly clear.

Got it. I like that name.. It's the name of one of my favorite Taucher songs. ;)

> **bingoUV said:**
> 
1. As I mentioned, use "nice" to start it. Even if it takes CPU resources, it will never block other processes if niced.

It's niced in /etc/rc.local so I should be good to go, right?

> **bingoUV said:**
> 
2. Update sometimes. Sorry I don't have an apt repository so you could get automatic updates. If somebody points out a defect in the script, or I find out myself, I'll update the code on that link. You can check last modification date on the page and decide. In fact I have made a minor change just 5 minutes ago ;). Doesn't impact you, don't worry.

I will check your site for updates regularly. You know what you could do, if you're going to do this for other problems regularly - set up a little mailing list we subscribe to and when you update something just shoot an email. But whatever works, I'll check it anyway.

> **bingoUV said:**
> 
3. Take a look at your CPU monitor. When gone crazy, this script takes 20% of my CPU. Add the "System Monitor" applet to your gnome panel. It will take care of all misbehaving applications : firefox, nautilus, video player etc.

I have System Monitor running all the time anyway so that works out. But what do you mean by "it will take care of" ...? It automajically takes care of runaway processes?

Edit: Not seeing a last modified date on the page. How 'bout just # it into the script? That's what I'm going to do to keep track.

---

### Post by bingoUV on 2008-08-16
This blog is going to become a blockbuster ;). Actually its grand opening ceremony was going to be tomorrow, but it was hastened because of you.

I strongly suspect comma in filename will not work. Otherwise I have tested with all common characters I could think of.

Yep, niced in /etc/rc.local should be enough.

Having system monitor always on should work great. I meant to say system-monitor will warn you about misbehaving processes, including this one. I was never the one to choose my words wisely.

It shows a modification date-time to me. Maybe only to the poster. I am new to blogging, see? I'll definitely add a last modification timestamp in GMT. Thanks for the suggestion.

---

### Post by Phases on 2008-08-16
Word, thanks again for all your help.

---


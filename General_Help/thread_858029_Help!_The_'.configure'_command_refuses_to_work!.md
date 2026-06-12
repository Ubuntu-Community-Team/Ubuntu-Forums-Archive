---
title: "Help! The './configure' command refuses to work!"
date: 2008-07-13
forum: General Help
---

### Post by J_Nathan on 2008-07-13
Please! I need help. I've downloaded a bunch of tarballs but every time I try to configure one (after unpacking it, of course) it just won't work. I installed synaptic packages like autoconf etc. but that didn't fix anything cause I still can't configure anything. All the help files etc. say to just type './configure' but they don't say what to do if it won't work. Does anyone out there know what i can do? Sorry if this is really vague.

Well, thanks a lot for your time and help,

---

### Post by PmDematagoda on 2008-07-13
Did you extract the archives and execute ./configure within the folders containing the extracted files?

---

### Post by Claus7 on 2008-07-13
Hello,

sometimes you have to have the right permissions in order to execute configure. If you type ls -l in the folder that comprises configure, can you see whether you are able to execute it or not?

Regards!

---

### Post by J_Nathan on 2008-07-13
Yeah, I did extract the package and then move to its directory before calling the './configure' command. Basically I learned how do that from this website called Tuxfiles.org. But thanks anyway, I really appriciate getting a response so soon!

---

### Post by kahlil88 on 2008-07-13
It sounds to me like you are new to compiling programs from the source code. A configure script checks your system for the programs that are required for the program you are compiling, and it will tell you when it is unable to find one. If there are no errors after running the configure script, you usually have to run **make** and then **make install**. If you're getting errors, please post them here and I (or someone else) will be able to assist you better.

---

### Post by J_Nathan on 2008-07-13
Thanks, Klaus7. I'll see if that's the case. But I just read the config.log file in the directory anh in said "/usr/bin/ld: crt1.o: No such file: No such file or directory" do you know what that means?

Well, all I can say is thanks again.

---

### Post by J_Nathan on 2008-07-13
Thanks Kahlil88! Attached here is the 'config.log' file those of you who are wise enough to understand it. I hope that's what you were asking for.

---

### Post by Claus7 on 2008-07-13
Hello,

sorry but I lost you a little. 
Firts things first.
It's not a good tactic to start compiling a program for yourself, concidering that you are in such a begginers state, that it's even difficult to you to navigate from folder to folder. Any way.

1) Download the tar packade to your desktop so as to have the same point of reference. That's easy I think. 
2)Now you can untar it I think also easily by 
clicking twice on it. Just click on ok and you will see a folder in your Desktop.
3)Navigate inside that foder via termial with :
cd Desktop/"name of folder"
4)Do an ls -l command. This will show you in columns the files and some information about them.
The first column shows the permissions. You have to have x's in oder to be able to execute the configure files. If you cannot see any then type :
chmod 755 configure
and try to execute the configure file as before.
Is it working?

About the message you get I do not follow you. So I propose you to do the above and see what will happen, exept if someone can give you a better guidance.

Regards!

---

### Post by Claus7 on 2008-07-13
Hello,

seeing the file I would suggest you to do :
sudo ./configure
and then give your root password,
because it sais that you cannot create executables...

Regards!

---

### Post by ChameleonDave on 2008-07-13
> **J_Nathan said:**
> Please! I need help. I've downloaded a bunch of tarballs but every time I try to configure one (after unpacking it, of course) it just won't work. I installed synaptic packages like autoconf etc. but that didn't fix anything cause I still can't configure anything. All the help files etc. say to just type './configure' but they don't say what to do if it won't work. Does anyone out there know what i can do? Sorry if this is really vague.

Well, thanks a lot for your time and help,
What do you mean it doesn't work?  That is so vague.  Is there no configure script?  Does the script fail to configure due to it lacking a dependency?  Until you provide this basic information, people will fire irrelevant solutions at you.

The best thing to do is to actually copy and paste the output you see on the terminal.

What is this "bunch of tarballs"?  Just provide a link to a single one of them, and we can look to see what the problem is.

---

### Post by ramjet_1953 on 2008-07-13
It very much sounds like you have not installed the [COLOR="Blue"]build-essential[/COLOR] package.
This is a meta-package that gives you all of the required tools for compiling.

[COLOR="Red"]sudo apt-get install build-essential[/COLOR]

Also it is highly recommended that you also install the [COLOR="Blue"]checkinstall[/COLOR] package
This is a package that creates a .deb package and allows you to load your newly compiled package with the debi package manager, making it much easier to maintain, or remove.

[COLOR="Red"]sudo apt-get install checkinstall[/COLOR]

I can't help but feel that you are biting off far more than you can chew at this stage.
Compiling from source requires many hours of study and practice to get your head around, especially when it comes to satisfying dependencies.

Just reading your post indicates that you have a lot to learn and you need to hit the books, before going much further.

Have you enabled all of the extra repositories in the package manager?
[COLOR="Blue"]Applications>Add/Remove [/COLOR]
When the window opens, use the drop-down menu in the top right-hand corner to select [COLOR="Blue"]All Available Applications[/COLOR].
You will then have a plethora of applications to play with, which are already compiled and ready to go.

Regards,
Roger :cool:

---


---
title: "Perplexing Persistant Permission Pain"
date: 2008-09-18
forum: General Help
---

### Post by JPman on 2008-09-18
****

I hate "permissions"!

Is anyone else in the world a "single user" in a household?    Every thing in my computer, since I deleted Balmer and Gates, belongs to me.   All the files in my computer belong to me.    Grrrrrr!

Is it possible for some bright kid to write a routine which will, when selected at boot, do work-arounds for everything that has to do with "permissions"?  That would be just sooooooo cool as the kids say.    I'm 66 years old and am hard pressed to accept that I must be enslaved to this requirement when I do not want it in my OS and I have no teenager in the house to fix it for me.

I do agree that restricted access to "admin" functions is a good idea but there is no one else in my house to share my computer with and honestly the stupid machine only does what it is programmed to do after all so why can't we allow for the single user who wants to simplify?

If I wanted this kind of pain I'd have stayed with M$.    To move to the much proclaimed Ubuntu and find this blatant lack of flexibility is something of a disappointment.

Now, please do not tell me in response to this about the wonders of "permissions" and how it is me and not the programming which is the trouble.  What I want is for the Ubuntu folks to see this post and give the idea some thought.

Is it not true that the only purpose of "permissions" is to insure user privacy?    OK then it is not always necessary.   Shouldn't it be up to the user?    

The access restrictions in my computer should have to do with protecting my OS against outside attack thus "admin p/w" is a good idea.   It should be up to me however whether or not I want to protect any of my personal files as well.   If anyone thinks "permissions" will keep federal hacks out of their files they deserve to get whatever they get.    Probably most high school kids have the system beat already but here I am stuck with it.   

And I don't even have any porn movies to hide either.

As info let me say that I have been to the "authorizations" menu and changed all the settings to "yes" to no avail.    The damn thing still tells me "I am not the owner....etc" which aggravates the hell out me.  I have read all the "help" files to no avail as well.    

One specific problem is my other HD from a previous version of Ubuntu.  This is an external USB HD.    It mounts OK but will not let me see my stuff.   I have discovered no way to fix this.    In my previous version I used the very same "user name" and p/w that I use now.    If I boot up Puppy Linux access is no problemo because the Pupster does not play the "permissions" game.   Using Puppy 3.01 I can go into any hard drive and t play.   I can move files into the Ubuntu file system manually and then when I reboot Ubuntu there they are like magic.   Because I can do this with Puppy Linux is proof to me that Ubuntu can do what I ask it do if someone at Cannonical just decides to do it and become the Linux leader they want to be.    Hey, how's that for an argument?

Why would it be so difficult to boot as a "single user" and bypass all permissions requirements, I mean just for that session?.    

Life would be so much easier for me.    I mean us old guys normally are too busy washing our Buicks or watching Lawrence Welk reruns to care about computers but here I am and I want to learn computers the "anti-Microsoft" way.   Paranoia about ordinary files is not my idea about "ease of use".

I hope no one is tempted to tell me that what I want can't be done because I know better.    And pleeeeeease don't tell me that, "most users want "permissions".   Business or shared computers users probably so but it's nothing but a large pain in the *** to me.

Thanks... I feel better now just for ranting.    Now I can have my coco and go to bed.  Heavens it's almost 7pm and I'm still up.

---

### Post by adult swim on 2008-09-18
while i have nothing to add to help you find a solution to your problems (except a shameless bump,) might i say, excellent execution of exuberant alliteration in your title!

---

### Post by iaculallad on 2008-09-18
As we all know, Linux in general has sets of users - an administrator and a user. With this grouping of user, it's with no doubt that permission will always be enforced per user/group. But even with the sets of permissions being applied, you as user can alter the permissions by using your terminal:

CHMOD
```
chmod ugo+rwx /mount-point/directory
```
CHOWN
```
chown -R user_name /mount-point/directory
```
CHGRP
```
chgrp group_name /mount-point/directory_or_file
```

Still, you could enable the root account and use it as default for your system (not recommended however).

---

### Post by JPman on 2008-09-18
> **adult swim said:**
> while i have nothing to add to help you find a solution to your problems (except a shameless bump,) might i say, excellent execution of exuberant alliteration in your title!
What?  Huh?    Wait.   Where did I put the dictionary?

---

### Post by JPman on 2008-09-18
> **iaculallad said:**
> As we all know, Linux in general has sets of users - an administrator and a user. With this grouping of user, it's with no doubt that permission will always be enforced per user/group. But even with the sets of permissions being applied, you as user can alter the permissions by using your terminal:

CHMOD
```
chmod ugo+rwx /mount-point/directory
```
CHOWN
```
chown -R user_name /mount-point/directory
```
CHGRP
```
chgrp group_name /mount-point/directory_or_file
```

Still, you could enable the root account and use it as default for your system (not recommended however).
Are those examples of "scripting"?    This is an area which I want to know more about as plainly better control can be exercised in this way.    Years ago I learned Basic and became quite used to being able to "list" my programs and change anything I didn't like.   Some time later commercial software arrived on the scene which was far better than anything I could write as an amateur.

It is very difficult but I have not seen a Linux book which is written in the same way as a standard college text.    This scholastic format, with exercises and lab practice, would lead the student in a more comprehensive way to full understanding of the subject.

Yes, most Linux (Linii?) are that way.   There is no reason for convention to become a biblical-like pillar which we dare not challenge.  

Thanks for the help.    I'll copy those and study them.   Right after Gilligan's Island.

---

### Post by y@w on 2008-09-18
While I understand your pain, I have to say something.. Permissions problems (namely perplexing persistent permission problems :) ) are a pain, yes, but they are also what keeps our data safe. What you're asking for can be done. In fact, it's called Windows 95. And.. actually.. I'm not kidding. Linux is by design a multi-user operating system. This confusion with permissions is not unique to Ubuntu and it's not even unique to Linux. 

You do mention that having an admin account is good to keep you safe on the web. However, since everything is essentially a file, this admin account has admin privileges by utilizing file permissions. Permissions confusions like this are definitely something to be overcome if Linux wants to hit mainstream desktop usage, but we can't have our cake and eat it too. 

I'd like to clear something up from your post for you if you don't mind. You mention having problems accessing a drive from a previous install of Linux even though you had the same username/password. Permissions on Linux have absolutely nothing to do with the username. It all goes by what's called the UID. It's a number associated with each account. The username is really just a display name that represents that number. You can plug in that hard drive and 'chown -R' the whole thing as yourself and you shouldn't have any issues using the files on that drive in Ubuntu. So the reason your old drive isn't going to work is because you most likely have different UID's from the old machine to the new. Puppy Linux does "play the game", you just have the correct UID when logged into that system.

---

### Post by mb_webguy on 2008-09-18
.

---

### Post by sloggerkhan on 2008-09-18
this should be relatively simple to solve from the gui....
do this:

alt-f2
type in gksudo gconf-editor
hit enter
use the tree-view menu to select / > apps > nautilus > preferences
check the box for show_advanced_permissions
close gconf-editor
alt-f2
gksudo nautilus
navigate to the mount point for the hard drive/folder in question
right click on it, select properties
go to permissions tab
set your user as owner and group
check boxes for whatever permissions you want the drive to have, 
hit apply to enclosed files

close window, close nautilus

you should now have permission to access the drive/folders/files

also, it is a BAD BAD BAD idea to do this to anything but storage directories you need access to, most of the system requires ownership by root or particular system users/groups to run properly.


w/regard to scripting,
those commands are just commands that can be executed in a shell or from the run menu.
A scripts is a document that contains many such commands arranged into a program and executed such that it is interpreted by a shell or script interpretor. 

Also, for documentation, remember, man [command name] gives you much info about a command.
You can use chown -R username:groupname and avoid the need for chgrp

Lastly, there are many tutorials for linux/unix commands and bash/shell scripting if you look for them on the internet. There ARE also textbook style books on such topics.

---

### Post by iaculallad on 2008-09-18
> **JPman said:**
> Are those examples of "scripting"?    This is an area which I want to know more about as plainly better control can be exercised in this way.    Years ago I learned Basic and became quite used to being able to "list" my programs and change anything I didn't like.   Some time later commercial software arrived on the scene which was far better than anything I could write as an amateur.

It is very difficult but I have not seen a Linux book which is written in the same way as a standard college text.    This scholastic format, with exercises and lab practice, would lead the student in a more comprehensive way to full understanding of the subject.

Yes, most Linux (Linii?) are that way.   There is no reason for convention to become a biblical-like pillar which we dare not challenge.  

Thanks for the help.    I'll copy those and study them.   Right after Gilligan's Island.

Those are terminal commands w/c will let you alter permission of folders and files but they can be incorporated to scripts for easier execution.

---

### Post by mb_webguy on 2008-09-18
> Now, please do not tell me in response to this about the wonders of "permissions" and how it is me and not the programming which is the trouble. What I want is for the Ubuntu folks to see this post and give the idea some thought.

With all due respect, it sounds like you don't fully understand file permissions -- either what they are intended to do, or how to use them.  Linux has been around for quite a while, and Unix -- the operating system from which Linux gets its concept of file permissions -- even longer.  A *lot* of people have given this a *lot* of thought, and the general consensus is that Unix-style file permissions are a Very Good Thing.

> Is it not true that the only purpose of "permissions" is to insure user privacy? OK then it is not always necessary. Shouldn't it be up to the user?

No, the primary purpose of permissions is *not* to ensure user privacy.  File permissions are the reason why Linux is the safe and secure operating system that Windows isn't.  File permissions prevent a user from accessing files the user shouldn't access, whether for privacy or security reasons.  And file permissions are up to the user.  You can change the file permissions on any and all files on your system.  Whether it's a good idea to do so is another matter entirely.

And you're actually *not* the only user on your computer, even if you're the only *human* user.

First of all, there's root.  In Ubuntu, this account is disabled so that you can't normally login to the account, but it still exists.  You use the root user's privileges whenever you're required to enter your login password to do something.  Some files and folders are owned by root, and other users don't (and shouldn't) have permission to change or sometimes even read these files and folders.  And this is a good thing -- it's part of what makes Linux safe from viruses, since unless a virus can somehow get root permissions, it can't do any serious damage to your computer.

Second, various programs you install may create their own user account.  This, again, is for your safety, since these programs may potentially allow access to your computer from the outside.  By running as a separate user without permissions to change your personal files, you are protected should some outside party manage to subvert these programs.

> If I wanted this kind of pain I'd have stayed with M$. To move to the much proclaimed Ubuntu and find this blatant lack of flexibility is something of a disappointment.

I find this comment confusing, since Windows doesn't really have *any* kind of file security, and also because Linux file permissions are about as flexible as you can get.  You can control exactly who has access to any particular file, as well as what kind of access they have.  How does that lack flexibility?

> Why would it be so difficult to boot as a "single user" and bypass all permissions requirements, I mean just for that session or as a default for all sessions?.

You can do that on most Linux distributions.  You just log in as root.  And if you sneeze or get a cramp while typing, you can trash your entire system.  That's why the root account is disabled by default on Ubuntu.

The concept of Linux file permissions can be daunting at first, especially when coming from a paradigm where nothing like that exists.  If you lived in a tent all of your life, the idea of solid doors with locks -- even if you have all of the keys to open those locks -- might seem insanely inconvenient.  However, once you realize how those doors and locks give you privacy and keep you safe -- and not just from others but from yourself, since some locked doors keep you out of dangerous areas -- then you might start wondering how you ever lived with tent-flaps.  And once you learn that opening a locked door is as simple as inserting the key and giving it a turn -- and that once unlocked, a door stays that way until you lock it -- doors with locks look a little less inconvenient.  In fact, once you get used to doors and locks and keys, using them doesn't seem like much effort at all.  A door with a lock is never going to be as simple as an open tent-flap, but once you understand the concept of doors with locks and the benefits they provide, you're not likely going to return to an open tent.

---

### Post by northern lights on 2008-09-18
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")
[http://www.psychocats.net/ubuntu/permissions]("http://www.psychocats.net/ubuntu/permissions")
[http://www.psychocats.net/ubuntu/security]("http://www.psychocats.net/ubuntu/security")

---


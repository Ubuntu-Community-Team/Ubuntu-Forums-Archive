---
title: "Maintaining updated software, how?"
date: 2008-07-28
forum: General Help
---

### Post by Tenn lynx on 2008-07-28
Hello fellow *buntu users!

My first post so yieeee!

Now on to my issue... 
So I recently decided to change my distro to ubuntu and I am overall very happy with it. I do have one concern however; there are some packages in synaptic that don't seem to get updated even though a new version of the program had been released some time ago... I can name Blender as one of these from the top of my head right now, but there are some other applications that I use and they have new releases out but no synaptic update.

Does synaptic get updates for certain things every 6 months or are these delays probably because of something else (like questionable stability or some other issue..)?

In any case, are there any general repositories that I could add that would be more "cutting edge"? I don't actually need all the new stuff out there that might potentially be full of bugs, but there are some apps that have cool features added or have some issues fixed and it would be !really cool! if I could just update everything with synaptic as opposed to having to build my own stuff outside of the -nice and orderly- package manager.

Maybe my obsessive-compulsion is acting up here hehe :)

Well, if anyone can explain the synaptic updating procedure that is used and if possible point me in the right direction for some updated stuff, that'd be great.


Regards
Tenn 

PS:
I know some projects like wine have their own repository, unfortunately amsn for example does not have one so...

---

### Post by northern lights on 2008-07-28
> **Tenn lynx said:**
> I know some projects like wine have their own repository, unfortunately amsn for example does not have one so...You've pointed the culprit out yourself. The issue is not Synaptic, but the sources that it uses, i.e. the Ubuntu repositories.

Ubuntu's main preference is user-friendliness and stability, so unfortunately that sometimes requires sacrifices in the time of implementation of a version.

Arch repositories, for instance, are pretty much updated right away. Most new version you'll have before you knew they existed. You'll also have to cope with a lot more maintenance work and required expertise to keep it running / get it to run in the first place.

Fortunately though, Ubuntu is Debian based, so finding a .deb of the version of preference is often not too hard. But if you want every program you use to be the latest released version, you'll have to end up compiling some things from source.

Notice I'm calling it 'the latest version' rather than the software being up to date, since quite often a new version is just a bugfix not even relevant to your hardware.

---

### Post by Tenn lynx on 2008-07-28
I see. Well I'll look into those arch repo-s, but since I'm only interested in certain things and am not looking to "update" everything I'll probably just keep finding the .deb packages for the things I really need updated...

Thank you for the clarification :)

---

### Post by steveneddy on 2008-07-28
Ubuntu will remain stable if you just wait for the repos to update.

I wonder what is so important that you need the newest version of that you can't wait a week or so?

---

### Post by northern lights on 2008-07-29
> **Tenn lynx said:**
> Well I'll look into those arch repo-s
Those are for Arch, they won't do jack sh*t for Ubuntu.
--> just meant as an example...

---

### Post by hyper_ch on 2008-07-29
ubuntu does (normally) not alter the version of a package in a given release. It will only add security fixes. This is not so much of a problem as you get a new ubuntu release every 6 months.

So in your case, what new features of blender do you absolutely need in the latest version that are not available in the one in the repos?

---

### Post by ad_267 on 2008-07-29
You could check if the newer version is in the hardy-backports repository. 

See here for more info: [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

You can enable backports in Synaptic under Settings - Repositories - Updates I think.

---

### Post by northern lights on 2008-07-29
> **hyper_ch said:**
> So in your case, what new features of blender do you absolutely need in the latest version that are not available in the one in the repos?
+1


> **ad_267 said:**
> You could check if the newer version is in the hardy-backports repository. 

See here for more info: [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

You can enable backports in Synaptic under Settings - Repositories - Updates I think.
While that's entirely true, I'd leave 'backports' disabled. 'Proposed' as well. Gonna get you into way more trouble than the advantage gained through a few newer versions, which might or might not be stable.

---


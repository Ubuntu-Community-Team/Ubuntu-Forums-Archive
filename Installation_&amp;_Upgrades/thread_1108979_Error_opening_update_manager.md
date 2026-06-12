---
title: "Error opening update manager"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by brayden13 on 2009-03-28
I get a error when I open it that looks like this:
```
Could not initialize the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '--2009-03-28' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list, E:The list of sources could not be read.'
```
I think I might have accidentally messed up a bit when trying to figure out how to get a DirectX app to run properly without all the errors. I was searching through the forum and there where some helpful things people had posted but sadly they might not have worked out very well.

So can anyone help me to get update manager working again?

P.S i just realised that even when i run synaptic package error i get
```
E: Type '--2009-03-28' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.


```
So I hope you guys can help me

Sorry but believe it or not i managed to fix my problem with minimal amounts of thinking. anyway what i did was try and delete the winehq.lists file. When I couldn't delete it through the File Browser i deleted it in terminal by doing these commands:
```
cd /
cd etc
cd apt
cd sources.list.d
sudo rm winehq.list

```
At least that problem is done with.

oh yeah and i do realise now that i did post in a ridiculously wrong section.

---

### Post by drs305 on 2009-03-28
Your source.list file has errors. Please post the results of:
```

cat /etc/apt/sources.list.d/winehq.list

```

If you don't or no longer use *wine* you could just delete the file /etc/apt/sources.list.d/winehq.list

---

### Post by Bucky Ball on 2009-03-28
Go to System->Administration->Software Sources and make sure you have the correct repositories checked. You may be requesting something from a repository that is not in your sources. If you have tried to do a suggestion from another page that requires you to download a package from a repository and that repository is not in your software sources, this is a likely outcome. Maybe check the page you were referencing again and make sure you haven't missed which repo they are downloading from. :)

As mentioned in last post, you could delete wine or add the the appropriate link in your software sources to access the appropriate repository.

---

### Post by Therion on 2009-03-28
Looks like you've modified your sources.list file?  Were you trying to add a repository or something?

Open a Terminal and cut and paste the output you get from using the following command:```
cat /etc/apt/sources.list
```

Methinks you have some rogue-code in that file that needs to be rooted out.

---

### Post by brayden13 on 2009-03-28
errr did you read the end of my post? well in the end i decided to delete that rotton winehq.list file. 
anyway the results from that command are:
#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

now i'm getting a little worried.

---

### Post by drs305 on 2009-03-28
> **brayden13 said:**
> errr did you read the end of my post? well in the end i decided to delete that rotton winehq.list file. 
now i'm getting a little worried.

A few things. Therion probably didn't see your edit. (If I change something in a post that might effect future posts I'll highlight it with bold or a color, but that is just me. The comment about why it was edited may be overlooked as well.

When you post a large output, it's best to put it between "code" tags. You do this by clicking on the # symbol while you are writing your post, then inserting the copy between the two tags.

Now, most importantly, why are you worried? The "rogue file" comment was in reference to your original unedited post, methinks. You fixed that.  ;-)

---

### Post by Bucky Ball on 2009-03-28
```
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid universe
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid universe
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-updates universe
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-updates universe
```Maybe comment this section out, go to your Software Sources in System->Admin and untick them if they are there. Then,

```
sudo apt-get update
```

---

### Post by brayden13 on 2009-03-28
I freak out to easily. Espcially when it comes to something like a OS. Oh well. I didn't mean to sound angry or anything. And I know the code tags are a better alternative. Just a bit of a rush i'm in.

In software sources i made it download from the main server.

when i update with the update command in terminal it doesn't download from aussie servers any more.

---

### Post by Bucky Ball on 2009-03-28
In Software Sources, where is says 'Download From' choose 'Other', then the selection to the right, 'Choose best server'. That should get you back to Aus and you may well find a speed improvement. I did using this method.

---

### Post by brayden13 on 2009-03-28
thanks. It did ping all servers but the best server wasn't very ideal after all. I just chose one based one the fact it was a FTP server from my favourite ISP.

---

### Post by Bucky Ball on 2009-03-28
Cool.

---


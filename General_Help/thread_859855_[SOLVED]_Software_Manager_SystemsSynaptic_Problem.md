---
title: "[SOLVED] Software Manager Systems/Synaptic Problem"
date: 2008-07-15
forum: General Help
---

### Post by barriel on 2008-07-15
I am an absolute newbie.Hence my problem. I was attempting to include the Medibuntu Packages on the Terminal and apparently "ran off the Rails".
When I attempted to get into Applications/Add-Remove I got the message- Major failure Software Manager system-check broken package with synaptic -check the file permissions & correctness of the file '/etc/apt/sources.list & reload software information with sudo apt-get update & sudo apt-get install -f
I tried this and got the message-
E: type'--11:15:38 is not known on line 1 in source list/etc/apt/source.list.d/medibuntu list

I went to Administration/ Synaptic Package Manager and received the same 11:15:38 message with the advice 
E: the list of sources could not be read go to respository dialogue & correct problem.
Please tell me how to solve this problem

---

### Post by mempman on 2008-07-15
> **barriel said:**
> I am an absolute newbie.Hence my problem. I was attempting to include the Medibuntu Packages on the Terminal and apparently "ran off the Rails".
When I attempted to get into Applications/Add-Remove I got the message- Major failure Software Manager system-check broken package with synaptic -check the file permissions & correctness of the file '/etc/apt/sources.list & reload software information with sudo apt-get update & sudo apt-get install -f
I tried this and got the message-
E: type'--11:15:38 is not known on line 1 in source list/etc/apt/source.list.d/medibuntu list

I went to Administration/ Synaptic Package Manager and received the same 11:15:38 message with the advice 
E: the list of sources could not be read go to respository dialogue & correct problem.
Please tell me how to solve this problem



This is what my /etc/apt/sources.list file looks like, make sure your looks similar (if you want you can just copy mines as I am running Hardy Heron):

```


# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy universe
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://repository.cairo-dock.org/ubuntu hardy cairo-dock

```


Furthermore, here are the permissions to the /etc/apt/sources.list file:
```

-rw-r--r-- 1 root 999 3108 2008-07-12 03:12 /etc/apt/sources.list

```

make sure that you have set your file up accordingly, after which you can run the following command:

```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by plucky on 2008-07-15
> **barriel said:**
> I am an absolute newbie.Hence my problem. I was attempting to include the Medibuntu Packages on the Terminal and apparently "ran off the Rails".
When I attempted to get into Applications/Add-Remove I got the message- Major failure Software Manager system-check broken package with synaptic -check the file permissions & correctness of the file '/etc/apt/sources.list & reload software information with sudo apt-get update & sudo apt-get install -f
I tried this and got the message-
E: type'--11:15:38 is not known on line 1 in source list/etc/apt/source.list.d/medibuntu list

I went to Administration/ Synaptic Package Manager and received the same 11:15:38 message with the advice 
E: the list of sources could not be read go to respository dialogue & correct problem.
Please tell me how to solve this problem

Your problem is not with your sources.list file but your medibuntu.list file.

Open a terminal and ```
sudo cp /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list.old
```

This makes a backup of the failing file.

Then assuming you are running Hardy 8.04 copy and paste the next two lines into a terminal window ```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
``` and then add the key ```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```


If you get no errors,then the Medibuntu repository should now be available.

Good Luck

---

### Post by barriel on 2008-07-15
Thanks for your response.As I said I am a complete Newbie.Sorry if this question sounds stupid,but how do I get to look at my /etc/apt/sources.list file?

---

### Post by iaculallad on 2008-07-15
> **barriel said:**
> Thanks for your response.As I said I am a complete Newbie.Sorry if this question sounds stupid,but how do I get to look at my /etc/apt/sources.list file?

On your terminal, issue the command below:

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by barriel on 2008-07-15
] have opened the file.Wherever [http://ca](http://ca) appeared,it now reads -http://au. 
Can I just alter it back to the way it was on the list. If so,How is it "saved"

---

### Post by plucky on 2008-07-15
> **barriel said:**
> ] have opened the file.Wherever [http://ca](http://ca) appeared,it now reads -http://au. 
Can I just alter it back to the way it was on the list. If so,How is it "saved"

You need to change the server **System > Administration > Software Sources** and select the "Other" in the "Download From" box and search for the best server for you.(Somewhere in California?)

When you exit select Reload and it should all update

Good Luck

---

### Post by barriel on 2008-07-15
Thanks Plucky.I attempted to do as you suggested.But I got the following messages-Could not download all repository indexes. The repository may no longer be available or could not be contacted because of network problems.If available an older version of the failed index will be used. Otherwise the repository will be ignored.Check your network connection & ensure the repository address in the preferences is correct.
 Then two error messages-
E: type"---18.35.31-- is not known on line 1 in source list/etc/apt/sources.list.d/medibuntu list
E unable to lock directory list
 The Second- E; type'---18.35.31--is not known on line 1 in source list/etc/apt/sources.list.d/medibuntu list
E THe list of sources could not be read.Go to the repository dialogue to correct the problem

---

### Post by plucky on 2008-07-15
> E: type"---18.35.31-- is not known on line 1 in source list/etc/apt/sources.list.d/medibuntu list
E unable to lock directory list


Do you have another synaptic package manager open?

Close all package managers and from a terminal ```
sudo apt-get update
``` and also post the output of ```
cat /etc/apt/sources.list.d/medibuntu.list
```


Good Luck

---

### Post by barriel on 2008-07-15
Sudo apt-get update gives the same error message--18.35.31 is no known etc


The second-
---18.35.31--http/www.medibuntu.org/source.list.d/hardy.list =>'hardy.list'
resolving [www.medibuntu.org---87.98.242.110](www.medibuntu.org---87.98.242.110)
connecting to [www.medibuntu.org|87.98.242.110|:80---connected](www.medibuntu.org|87.98.242.110|:80---connected)
http request sent,awaiting response---404 not found
18.35.33 error 404: not found.
Is it possible to just delete the Medibuntu package. I can live without it?

Sorry for the stupid questions
I have noticed on my etc/apt/sources.list that their is no mention of a Repository address

---

### Post by plucky on 2008-07-15
> I have noticed on my etc/apt/sources.list that their is no mention of a Repository address 


That is because it is not there.It is in **/etc/apt/sources.list.d/** notice the **.d**.

There have been other posts on the forum about being unable to access the Medibuntu repository in the last couple of days.They seem to be rebuilding the site.

The last command should have produced ```
## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ hardy free non-free
# deb-src http://packages.medibuntu.org/ hardy free non-free
```


It is possible the other two commands didn't work.Well I just tried an update and that was ok so I am not sure what is happening with your system.

Try this command in a terminal ```
cd /etc/apt/sources.list.d/
ls -l
``` and it should have medibuntu.list as a file.If it is there,you can delete it with ```
sudo rm medibuntu.list
``` then try ```
sudo apt-get update
sudo apt-get install -f
``` and see if that works.

Good Luck

---

### Post by barriel on 2008-07-15
[http://ubuntuforums.org/attachment.php?attachmentid=77862&d=1216165776](http://ubuntuforums.org/attachment.php?attachmentid=77862&d=1216165776)

this is the response to the first command

---

### Post by oldos2er on 2008-07-16
It looks like you ran "cd /etc/apt/sources.list.d/ ls -l" as one command. It should be two separate commands.

 If you run "gksudo gedit /etc/apt/source.list.d/medibuntu list" in a terminal, you can comment out the offending line(s).

---

### Post by barriel on 2008-07-16
Thank you all for your contributions to solve my problem. I have learnt my lesson and I will not jump in again without knowing what I am doing.
Plucky
Mempman
Iacullad
Oldos2er

Best Regards
[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---


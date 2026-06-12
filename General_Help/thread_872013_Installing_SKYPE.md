---
title: "Installing SKYPE"
date: 2008-07-27
forum: General Help
---

### Post by NeoAndersen on 2008-07-27
Hello!!
I've tried to install skype using these tips:
   To add the Skype repository, click System &#10148; Administration &#10148; Software Sources. Click
the Third Party tab in the window that appears, and then click the Add button. In the APT
Line text box, type the following:
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
   Note the spaces between debian/ and stable and between stable and non-free.
   Then click the Add Source button. Click Close, and click the Reload button on the
dialog box that appears.
   To install Skype, open Synaptic Package Manager (System &#10148; Administration), click
Search, and type skype into the search box. Then click Search. In the list of results, put a
check alongside the entry, and click Mark for Installation. You’ll see an error message
about Skype not being authenticated and that an additional package needs to be installed,
but this is acceptable, so click the Mark button on the dialog box. Then click Apply on the
toolbar to install the software.
   Once the software has installed, click Applications &#10148; Internet &#10148; Skype to start it.

  THE PROBLEM IS:

When I click the Reload button a error message appears: "Could not download all repository indexes"

I am using Ubuntu - 8.04.1 - desketop - amd64
I am a beginner in linux.

---

### Post by Ryadt on 2008-07-27
Try in terminal```
sudo apt-get install skype
```

---

### Post by NeoAndersen on 2008-07-27
I've just tried and don't work...
Thank you anyway...

---

### Post by ryanhaigh on 2008-07-27
If you are using 64bit ubuntu try these instructions:

[https://help.ubuntu.com/community/Skype#AMD64](https://help.ubuntu.com/community/Skype#AMD64)

---

### Post by jonian_g on 2008-07-27
Skype doesn't have 64bit support, so you have to force the installation of the 32bit package and install some libraries or you could download the static package of skype from here:

[http://www.skype.com/go/getskype-linux-static](http://www.skype.com/go/getskype-linux-static) (sorry for the direct link)

extract it, open the folder and double click the skype executable and you're ready to use skype.

Then if you want you can move that folder in your home directory and create a launcher in the Applications menu or the panel.

---

### Post by NeoAndersen on 2008-07-28
It was really easy to install the static version of skype but when I tried access a skypecast a message appeared: Skype version 3.2 or later needed, then I will continue trying to intall the last version because I use skype firstly to practice English in skypecasts... Then thank you anyway!!
 
As I said I am a beginner in linux and seems to me that to install the other option I must know something about terminal... 
I followed these tips:
For 8.04:

   1. Install the ia32-libs package (from universe component)
   2.

      Download Skype package for Ubuntu ([http://skype.com/download/skype/linux/](http://skype.com/download/skype/linux/))
   3.

      Install it: sudo dpkg --install --force-architecture --force-depends <downloaded_package> 

When I went to install the ia32-libs I discovered in synaptics that it was installed already... So I downloaded the package for Ubuntu from the skype site. But in the terminal a error message appeared as follows:

neoandersen@neoandersen-desktop:~$ sudo dpkg --install --force-architecture --force-depends skype-debian_2.0.0.72-1_i386.deb
dpkg: erro processando skype-debian_2.0.0.72-1_i386.deb (--install):
 impossível acessar arquivo: No such file or directory
Erros foram encontrados durante processamento de:
 skype-debian_2.0.0.72-1_i386.deb
neoandersen@neoandersen-desktop:~$ 


I guess there is something missing in this comand: sudo dpkg --install --force-architecture --force-depends skype-debian_2.0.0.72-1_i386.deb


 skype-debian_2.0.0.72-1_i386.deb is the package name I downloaded and saved on desktop.

How can I solve this?

---

### Post by ryanhaigh on 2008-07-28
You need to execute that command in the same directory that the downloaded file is in, which is probably your desktop, the easiest thing to do would be copy the file into your home directory.

I have to point out though that the statically linked and deb versions of skype are the same version so you are going to get the same error once it is installed and you won't be able to do the skypecast.

---

### Post by dentaku65 on 2008-07-28
You must add Medibuntu repositories
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Then:
```
sudo apt-get install skype
```

---

### Post by ryanhaigh on 2008-07-28
> **dentaku65 said:**
> You must add Medibuntu repositories
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Then:
```
sudo apt-get install skype
```

A quick look here: [http://packages.medibuntu.org/pool/non-free/s/skype/](http://packages.medibuntu.org/pool/non-free/s/skype/) indicates that the versions provided by medibuntu are the same as those provided by skype so you still will not be able to do skypecast, however it will make updating to the later version easier (when the eventually become available)

---

### Post by jonian_g on 2008-07-28
Skype version 2 is the latest for linux, there is no version 3.2 for linux.
It would be better if you asked the skype forums if you can use skypecast on linux.

---

### Post by NeoAndersen on 2008-07-28
Hello!!

I managed to install Skype 2.0 this way:
I installed my proper Medibuntu repository (Ubuntu 8.04 "Hardy Heron") entering this command:

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

Then following the instructions in the medibuntu page ([https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)) I added the GPG Key with this command:

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 

Finally I went to Applications &#10148; Internet &#10148; and there was the Skype icon.


A friend sent me a skypecast number so I could listen them!!! But I dont know if I will be able to speak to them too, because my headphone wasn't connected... But I couldn't join a skypecast clicking directly from the skypecast page...

Are there a program in linux that can work like skype on skypecasts?
I like the skypecasts' possibilities very much... If I could create programs I would begin working in a project like skypecast just now!!!

We must have in linux and Ubuntu our kind of skypecasts!!!
Just because I don't want dual boot anymore...

Thank you for the help!!!

---

### Post by VMC on 2008-07-29
Under Options > Sound Devices use the "Make a test call" to the right. It will test your audio and allow you to record a test call for your voice options.

---

### Post by NeoAndersen on 2008-08-24
I am using skypecasts daily...
All I have to do is discover the number of the skypecast I want to enter and  call it...
I can find this number going to the skypecast page I want to participate, then I login in, and go to the mozilla firefox View menu and then I click in Page Source to see it. Now I must find the number in the middle of a lot of Page Source information that appears...

The line with the number is about in the middle of the page:

<p class="start">
                                 
		            <a href="#join" onClick="joinCast('[COLOR="Red"]+9900111926237167324[/COLOR]?call&token=5361717&amp;topic=South+Africans+Only')">Join this Skypecast</a>
                                        </a>
            </td>
    <td>

The number will just appears if you are logged in on the skypecast page.

Now all you have to do is to call this number. But you will not have the knobs to ask to talk neither to mute you mic for instance...
So you must type a message to the host or to somebody in the speaking area to ask the host to put you to speak. Only the host can right click you and put you up in the speaking area.

But it is impossible to host a skypecast with this 2.0 version of skype...

---

### Post by NeoAndersen on 2009-11-05
Things are easier now...

I've just installed "Skype Ubuntu 8.10+ 64-bit"
on Ubuntu 9.10...

All I had to do was to download it:
[http://www.skype.com/intl/pt/download/skype/linux/choose/]("http://www.skype.com/intl/pt/download/skype/linux/choose/")

and click in it that the package installer take care of everything...

But the version is still  2.1.0.47

---


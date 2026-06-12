---
title: "OpenOffice 3.0.1?"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by RamonS2007 on 2009-02-21
Hi!
After some time I came back to Ubuntu and now try to replace the old 2.4 version included in 8.10 with OOo 3.0.1. I downloaded the deb packages, but run into some issues (unsatisfied dependencies) as I have no clue in which order the packages need to be installed. Also, I was not able to add the downloaded packages to Synaptics in order to have the package manager do the dependency resolution for me, since I assume Synaptics to be smarter than me. So, the question is:
How do I install OpenOffice 3.0,1 on a stock 8.10 install?

Related to this, why is it that all repositories tend to provide only applications versions that are from Yurassic Park? At least in case of OpenOffice there are current deb packages available, so I am confused why the Ubuntu repositiories only offer 2.4. Back when I first used Ubuntu the same issue was with Firefox, but that seems to have been cleared up and after updating the stock packages I now have the current Firefox version.

Asking a bit more generally, if I can get a hold of Debian packages (or RPMs that get converted to debs), what is the best approach to install them or use them to update  existing apps? Installing binaries on Ubuntu should not be that difficult.

Any advice is greatly appreciated.

---

### Post by ddarsow on 2009-02-21
in a terminal, change to the directory which contains the .deb file and then enter:

sudo dpkg -i *.deb

---

### Post by rjstep3 on 2009-02-22
I am trying to do that too, but using sudo dpkg -i *.deb results in

dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb

No idea what that means, but help would be appreciated to get 3.0.1 installed!!

I also don't understand why the repositories only have the old version ...

rjstep3

---

### Post by 00b00nt00 on 2009-02-22
See this web page:

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by rjstep3 on 2009-02-22
wow thanks, that worked.

Question remains - why did my 

sudo dpkg -i *.deb 

not work?

thanks for the help!!

rjstep3

---

### Post by rmikel on 2009-02-24
**Solution:**

The following steps worked for me.

1. in Synaptic pakage manager, uninstall all open office pakages including the core.

The reason for this is that I found that when I tried to install/update the Open Office suite Synaptic says that it conflicts with the open office core pakage. Even though the pakage is way out of date.


2. With the Synaptic pakage manager, go to the downloaded open office 3.0.1 pakage go to the folder titled "DEBS" or similarly marked.

3. From the Synaptic pakage manager, install the pakage containing all in the name.

4.0 Go to the panel and see if Open Office 3.0.1 was installed.

---

### Post by RamonS2007 on 2009-02-24
I tried the instructions from the web site and it works. Thank you very much for pointing to that resource!

But now to my more general question: Why on earth does this have to be so needlessly complicated?

I am not a novice user and the process itself is not that complicated, but where the heck is anyone supposed to get the "deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main" line from?

To make Ubuntu and Linux in general easier these things need to be automated better. I know that the 'blame' goes to the OOo folks as well, and, yes, the user, too. I could have just spent the hours on the web trying to find the answer myself, or I could just be so well-versed in package managers (there are way too many) that I can figure it out myself. Well, since I want to use the system rather than re-engineer it time constraints come into play.

I admit that I am also a Windows user and the brainless "download exe, click on it, be done with the install" approach is just easier. I don't say it is better in all dimensions, just easier and thus better to use. And it really is a shame, because package managers like Synaptics really have come a long way.

With that, is there any project cooking in Ubuntu-land that attempts to make obtaining new software easier? Any chance to help along getting newer apps into the standard repositories faster?

Am I asking too many questions? Anyone mind some popcorn? :popcorn:

---

### Post by OutOfReach on 2009-02-24
> **rjstep3 said:**
> wow thanks, that worked.

Question remains - why did my 

sudo dpkg -i *.deb 

not work?

thanks for the help!!

rjstep3

Did you change to the directory containing the debs before you did that? If not, that was probably it.

---

### Post by scouser73 on 2009-02-25
I made a tutorial for installing OpenOffice 3.0.1 which can be found here; [http://ubuntuforums.org/showthread.php?p=6639054#post6639054]("http://ubuntuforums.org/showthread.php?p=6639054#post6639054")

---

### Post by wildmanne39 on 2009-02-26
Hi thank you so much for your instructions, I get this error and I hve place the file on the desktop. I am using 64 bit kubuntu. Any help will be greatly appreciated.

---

### Post by rjstep3 on 2009-03-02
the instructions worked just fine for me - everything is now up and running beautifully.

thanks
rjstep3

---

### Post by Colinho on 2009-03-12
Hi, I'm having some trouble installing OpenOffice 3.0.1

I can extract, navigate to the DEBS directory, and use the "sudo dpkg -i *.deb" code. It goes through "Preparing to replace xxxxxx" and "Unpacking replacement xxxxxx"for each package. It then does "Setting up xxxxxx" for all the packages but the problem I have is that it says "Processing triggers for menu..." and stays like that, without doing anything. The entry line (don't know the proper word for it:( ) comes up - "colin@colin-desktop:~/Desktop/OOO300_m15_native_packed-1_en-US.9379/DEBS$" and nothing is installed.

It doesn't seem like a major problem, but my Novice troubleshooting hasn't been able to help me so far. Any help would be much appreciated ^^

Cheers :D

EDIT: Whoops my bad, all that was needed was the desktop integration to be installed. Figured that out about a minute after posting ^^
But I will still leave my post here so other novices who think they have a problem like I did can see what to do.

But I do think that they could make installing OOo a little less tedious <.<

---


---
title: "Skype??"
date: 2005-12-06
forum: General Help
---

### Post by acaus on 2005-12-06
No matter what I try I cannot get Skype to work? Any help will be appreciated!!I have it in the applications list but nothing happens when I click on it.

Thanks

---

### Post by WebDrake on 2005-12-06
[QUOTE=acaus]No matter what I try I cannot get Skype to work? Any help will be appreciated!!I have it in the applications list but nothing happens when I click on it.[/QUOTE]
From my own experience, it takes quite a bit longer to start up than one would have expected.  But can you start it from a terminal?  Open terminal, type,

skype &

and see what happens.  Maybe that will give more clues.

---

### Post by acaus on 2005-12-06
Tried your suggestion this is what happened.

skype: error while loading shared libraries: libqt-mt.so.3: cannot open shared o bject file: No such file or directory
[1] 10397
[1]   Exit 127                skype


Cheers

---

### Post by WebDrake on 2005-12-06
Sounds like you're missing a necessary library file.  Try searching through the Synaptic package manager for the library in question, and installing it.

Actually now I think about it I seem to remember having a similar problem, but I can't remember exactly how I fixed it.  However, the following page: [http://homex.subnet.at/~max/ubuntu/](http://homex.subnet.at/~max/ubuntu/) seems to correspond to what I think I did.  Search that page for "libqt" or "Skype" and you should find the useful info.

---

### Post by Bandit on 2005-12-06
I am not saying dont use Skype, as it is very popular and well rounded. But have you tried Gnome Meeting? It performes faster then skype due to its direct connection making both sound (VoIP) and video much faster.
Cheers,
Joey

---

### Post by MetalHannes on 2005-12-06
So can you connect with Gnome meeting to a skype server??

Hannes

---

### Post by Bandit on 2005-12-06
[QUOTE=MetalHannes]So can you connect with Gnome meeting to a skype server??

Hannes[/QUOTE]
I think there is a way. I was doing alot of reading on it yesterday. I cant remember if they added it already or its in the works. I do know it is multiprotocal so you are not limited on your sorces. here is the homepage [http://www.gnomemeeting.org](http://www.gnomemeeting.org) 
Latest version is 1.2.2 and its on the Ubuntu CD install.
Cheers,
Joey

---

### Post by henriquemaia on 2005-12-06
[QUOTE=Bandit]I think there is a way. I was doing alot of reading on it yesterday. I cant remember if they added it already or its in the works. I do know it is multiprotocal so you are not limited on your sorces. here is the homepage [http://www.gnomemeeting.org](http://www.gnomemeeting.org) 
Latest version is 1.2.2 and its on the Ubuntu CD install.
Cheers,
Joey[/QUOTE]

I have found this on their website, on the faq:

> 1.1.4. What is it compatible with?

GnomeMeeting is supporting H.323 which is the major protocol for VoIP, IP Telephony and videoconferencing. It will thus be compatible with all H.323 softphones and hardware IP Phones. A few example are MyPhone, Netmeeting, CuSeeMe, OpenPhone, SJPhone, SwissVoice IP Phones, ... Work is being done in CVS to also support SIP and bring compatibility with other software. **GnomeMeeting is not compatible with Skype and will never be as long as their protocol will stay proprietary**. We do not think using closed protocols for communications is a good thing, that's like if some web browsers were only able to browse given websites respecting a closed protocol. That's clearly not the future.


---

### Post by acaus on 2005-12-06
[QUOTE=WebDrake]Sounds like you're missing a necessary library file.  Try searching through the Synaptic package manager for the library in question, and installing it.

Actually now I think about it I seem to remember having a similar problem, but I can't remember exactly how I fixed it.  However, the following page: [http://homex.subnet.at/~max/ubuntu/](http://homex.subnet.at/~max/ubuntu/) seems to correspond to what I think I did.  Search that page for "libqt" or "Skype" and you should find the useful info.[/QUOTE]
 I tried to find the package in the Synaptic Package manager and could not find it?? I use Skype for alot of my friends do!! I have used it in Windows for a year and if I can't get it to work here, I will have to go back, but I don't want to!!

---

### Post by henriquemaia on 2005-12-07
[QUOTE=acaus]I tried to find the package in the Synaptic Package manager and could not find it?? I use Skype for alot of my friends do!! I have used it in Windows for a year and if I can't get it to work here, I will have to go back, but I don't want to!![/QUOTE]

Read this thread:

[http://ubuntuforums.org/showthread.php?t=80295]("http://ubuntuforums.org/showthread.php?t=80295")

Automatix makes skype available for you, very easily.

---

### Post by Gray. on 2005-12-07
You'll have to use [EasyBreezy]("http://dev.realistanew.com/easybreezy/easybreezy0.33-alpha.tar.gz"), now that Automatix is no longer available. Insructions on how to install it are [here]("http://www.ubuntuforums.org/showthread.php?t=100250"), the third post.

---

### Post by omegamike on 2005-12-07
If the auto installs don't work, and you still want to use Skype, you might try downloading the Mandriva .rpm on the skype site and convert it to a .deb package. I too had trouble with dependencies when it came to downloading the Debian package. So what you would do is download the Mandriva .rpm, then go to the terminal:

cd /home/username/locationwhereyousavedthefile
sudo alien -t thenameoftheskypefile.rpm

then keep track of what it saves the new file as. it should be in the same directory, then

sudo alien thenameofthenew.tar.gz

then install

sudo dpkg -i thenameofthenew.deb

Note:You will have to have some sort of qt libraries on your system! If you don't have alien you would have to get that as well:

sudo apt-get install alien

This works if you are wanting to avoid using one of the other installation programs

---

### Post by WebDrake on 2005-12-07
[QUOTE=Bandit]I am not saying dont use Skype, as it is very popular and well rounded. But have you tried Gnome Meeting? It performes faster then skype due to its direct connection making both sound (VoIP) and video much faster.[/QUOTE]
In principle I would love to use it; but it just doesn't have the same feel of professionalism as Skype does.  When, for example, I clicked on the link to apply for a PC-to-phone account, I was sent to a website I'd never heard of, with no obvious link to Gnome Meeting, with no warning that this was going to happen.

... not exactly a confidence builder, IMO.  Whereas Skype does everything themselves, and makes everything very clear, when it comes to actually paying money.

In theory there are all sorts of good reasons to go with an open-source, open-protocol method like Gnome Meeting, but where things involving exchange of money are concerned, one should expect a certain minimum standard of clarity and service which I just don't see here.

---

### Post by robotgeek on 2005-12-08
[QUOTE=Gray.]You'll have to use [EasyBreezy]("http://dev.realistanew.com/easybreezy/easybreezy0.33-alpha.tar.gz"), now that Automatix is no longer available. Insructions on how to install it are [here]("http://www.ubuntuforums.org/showthread.php?t=100250"), the third post.[/QUOTE]

H, currently there is a bug with the skype installation in EasyBreezy (i.e it does not appear in the menu). However, you can still manually launch skype by /opt/skype-1.2.0.18/skype &

You can file bugs (for now at [http://easybreezy.robotgeek.org](http://easybreezy.robotgeek.org) or by dropping in at #easybreezy on irc.freenode.net)

---


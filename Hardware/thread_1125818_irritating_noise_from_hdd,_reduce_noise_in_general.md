---
title: "irritating noise from hdd, reduce noise in general"
date: 2009-04-14
forum: Hardware
---

### Post by Claus7 on 2009-04-14
Hello,

I have an old computer compared with the machines that they are out today. What it troubles me is the noise that it produces. I would like to reduce it, because it is really annoying. 

The first thing I would target are the fans. This said, I do not think that it will be difficult to change them.

What it bothers me is the noise from the hdds. I bought one recently for a clean install of jaunty. Things went ok, yet from time to time there is a buzzing noise that comes out from the new hdd. For the old one I think that I cannot do anything. So my questions are:

i)have you faced similar noise problems and if affirmative, how do you decided to solve them?
ii)Should I worry about the periodic noise (buzz) of my new hdd? Does this mean that it has some problems or is it a normal situation for hds?
iii)which part of your pc contributes most to the noise your pc produces?

Regards!

---

### Post by ddrichardson on 2009-04-15
Buzzing noises are usually interference, check there are no leads contacting moving parts - especially cables connected to the soundcard or onboard speaker.

If, however you mean a humming noise - then you can deal with that by making sure the screws are tight and if it persists damp the vibration by using rubber washers.

Fans are normally the most noisy - but airflow is a combination of speed and fan size, a big fan with a good heatsink can be spun at a lower speed which tends to be quieter.

That said, the biggest noise problem is an unbalanced fan - which is surprisingly easy if you store the unit on the floor where it picks up more dust, which clogs the fan blades and throws them off balance. The more the balance is off, the more wear on the bearings.

---

### Post by Claus7 on 2009-04-23
Hello,

at first thank you for your answer. The problem of the noise seems to be the independent components of the pc rather than cables e.t.c.. I took another cpu fan and I have to say that I regreted it a little. The noise remains almost the same. It has to do like a small whistle, which is very irritating. Also there comes vibration from the sata hdd, which is the same as that of an external one. 

No cable is interfering with any of the fans. The vibration noise disappears if I apply force above the computer or at random during operation.

Yet, I think that someone can benefit from the experience I got changing my fan.

A lot of people have new pcs with towers that cover half of their rooms, graphics cards that can play the latest games in town e.t.c e.t.c..

My computer is a "normal" one without all this fancy things. Because it is noisy, I thought that I had to change the fan of the cpu. In order for someone to change that fan, someone has to know the socket of the motherboard, so as to be able to choose the right cpu cooling system. Mostly the cooling system is comprised by a fan and a lot of piece of metal. The socket has to do with the base around the cpu, where the fan and the piece of metal are attached so as to cool the cpu unit. In order for someone to identify the socket, someone has to go and look the specs of the motherboard.

Have in mind that the cooling system (cs) is huge, and some of them if they do not have fans (completely noise free, yet cost more) then they are even more huge. 

The process of removing the old cs and put a new one, depends on the box one has. Maybe you have to remove some components, which even though they have nothing to do with the cs, they do not allow you to see well how to place the new cs. I had to remove the power supply in order to put the cs. 

Other than the above I'm still trying to find out how to reduce the noise of my pc. I think that it is very irritating to work and hear a whistle every moment that passes by.

Regards!

---

### Post by Claus7 on 2009-04-25
Hello,

the problem finally was an old hdd! The noise had to do with a whining like a fridge (I do not know how to describe it best). Now I'm thinking of disabling that disk, yet I do not know exactly how I will tamper with grub so as to open only the new hdd.

Regards!

---

### Post by ddrichardson on 2009-04-25
Sounds like a shot bearing. The noise will still be present unless you remove the power to the drive.

---

### Post by Claus7 on 2009-04-25
Hello,

yup! I know I have to remove it, yet not now, because I have still some data I need to it. I came across this post:
[http://ubuntuforums.org/showpost.php?p=3748949&postcount=2](http://ubuntuforums.org/showpost.php?p=3748949&postcount=2)
which seems very helpful as to put grub loader in the disk I'll keep.

Could you tell me, ddrichardson, what shot bearing means? I have not come across this again and I have a vague idea of what it might mean. Google doesn't seem to help either.

Thanks,
Regards!

---

### Post by pbpersson on 2009-04-25
> **Claus7 said:**
> 

Could you tell me, ddrichardson, what shot bearing means? I have not come across this again and I have a vague idea of what it might mean. Google doesn't seem to help either.

[http://en.wikipedia.org/wiki/Ball_bearing]("http://en.wikipedia.org/wiki/Ball_bearing")

---

### Post by ddrichardson on 2009-04-25
Bearings are used to allow to components to rotate without friction causing them to overheat. There are several bearing types but in all of them if you get dirt ingress then it causes the path of rotation to fall out of alignment and makes the noise you describe.

Shot is a thoroughly non-technical term meaning broken nut infinitely more polite than the more common four letter derivative.

---

### Post by ddrichardson on 2009-04-25
Indecently, a lot of modern drives use fluid bearings. They're quieter.

---

### Post by Claus7 on 2009-04-25
Hello,

thank you for your immediate and really very explanatory answers. It clarified a lot! Now, is it possible I can change this bearings or is it too risky for someone to change those in a hdd?

Regards!

---

### Post by ddrichardson on 2009-04-25
Not a chance, forget it. Hard disks are cheap enough that its not worth the effort. If its a fluid bearing you haven't the facilities and if its a ball bearing then you'd need the right greases and diameter balls if one is damaged. It would also be incredibly fiddly and I don't think they're designed for replacement.

Its difficult to get access to and if it goes wrong it'd most likely heat to destruction.

Besides if the bearings are worn and that's causing the noise the drives life in its landing cycles is probably high too.

---

### Post by Claus7 on 2009-04-26
Hello,

this is what I was expecting. Thanks for the info. I just want to add that I knew the ball bearings with their french counterpart which is: roulement 
(in hellenic &#961;&#959;&#965;&#955;&#949;&#956;&#940;&#957;)
[http://images.google.com/images?hl=en&client=opera&rls=en&um=1&ei=bUT0Scy1KcOQjAeZ1IXLDA&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=roulement&spell=1](http://images.google.com/images?hl=en&client=opera&rls=en&um=1&ei=bUT0Scy1KcOQjAeZ1IXLDA&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=roulement&spell=1)

Regards!

---

### Post by KhurramM on 2009-04-26
I suggest u stay away from the bearing change.

Its not worth to do.

Better get a new hdd instead.

---

### Post by Wiebelhaus on 2009-04-26
Old hard drives chatter and that often indicates approaching problems , the techincal term for it is "Excessive Drive thrashing" Replace the old crappy drive with the cheapest new one from [www.newegg.com](www.newegg.com) you can find.

---

### Post by Claus7 on 2009-04-27
Hello,

I can see a lot of responses for this subject. It is very irksome sometimes the noise that someone gets from someone's pc. Just a notice. It might not be any of the above. I mean that it might not be a faulty hdd, yet just the series of the hdd. For example there might be some models, that for some reason they are noisy. This does not mean that they are faulty ones, yet, that they were just made that way.

Now, because I have seen a lot of interest, I would like to give ubuntu a credit in a similar issue.

Just try to do search from a windows box and a linux machine to the same hdd. In the one in question, trying from windows, I have to say that it makes a "scratch" noise while it is searching (and not only doing that action). From ubuntu, the only time I remember doing that noise, it was when I made a fresh install to my new hdd the first very moments of the installation. Other than that, both the old hdd and the new one, are "scratch noise free" as one can get. 

I say this just if someone comes across this thread and recognizes the same "symptoms" as I had.

Regards!

---

### Post by Claus7 on 2009-04-27
Hello,

continuing this thread I would like to add this:

i)typed
sudo grub

and in the command prompt typed:
find /boot/grub/stage1

which resulted in:
   (hd0,1)

I did then:
root (hd0,1)

and finally:
setup (hd1)

so as to install grub to my second hdd.
The process went ok without errors [the setup (hd1,0) command gave some errors].

Now, if I want to unplug my hd0, grub complains with an error. Is it possible to put my old hdd to "rest" and be able to plug it whenever I wish, without having grub errors?

Regards!

---

### Post by Claus7 on 2009-05-02
Hello,

I have not fixed yet the issue, yet this is how I can get up to now:

the error I get when I unplug the power from the hdd is:
GRUB Hard Disk Error

Searching a little about it ([http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting)) I saw that it has to do with:
The stage2 or stage1.5 is being read from a hard disk, and the attempt to determine the size and geometry of the hard disk failed.

This is not something "weird" as with the previous process I had "copied" the grub data from my old hdd to the new one.

No if it fails because it cannot see the old hdd or because some data transfered during the process are not valid any more it remains to be seen.

Maybe it has to do with an old BIOS too, yet I cannot change anything in BIOS as there is no new version.

edit:In some of the updates I was informed that grub was not the one it should be, so automaticaly it changed. Other than that the new disk is in ext4 and the old one in ext3 and while searching the net I saw that this might cause some issues.

Regards!

---

### Post by Claus7 on 2009-05-09
Hello,

problem solved here:
[http://ubuntuforums.org/showthread.php?p=7248420#post7248420](http://ubuntuforums.org/showthread.php?p=7248420#post7248420)

edit:as I understood with root I had to choose the hdd and partition where I wanted to install grub.

Regards!

---


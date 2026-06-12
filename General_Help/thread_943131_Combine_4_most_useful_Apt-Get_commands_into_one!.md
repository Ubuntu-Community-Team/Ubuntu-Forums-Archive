---
title: "Combine 4 most useful Apt-Get commands into one!"
date: 2008-10-09
forum: General Help
---

### Post by Saint Angeles on 2008-10-09
(EDITED on 10/24/08 )

i have just made a bash script that allows me to run
```
apt-get check
apt-get update
apt-get dist-upgrade
apt-get autoclean
apt-get autoremove
```in one bash script. all i have to do is type ```
apt5
``` into a command prompt and the commands will be run. (it used to be 4 commands until somebody suggested i also add "apt-get check". now its 5.

heres how I did it:

WARNING: this will update every package on your computer including the kernel and xorg. it is possible this could lead to breakages so be careful and read everything in the terminal before agreeing to update.

1) i created a directory in my home folder called "bash" (~/bash). This is where I want to copy all custom bash scripts into.
2) I created a file called "updateall" (without quotes) and I put the file into this bash directory. What I wrote into "updateall" is this:
```
#!/bin/bash
#script to run several apt-get commands at once!

apt-get check &&

apt-get update &&

apt-get dist-upgrade &&

apt-get autoremove --purge &&

apt-get autoclean
```I saved it. so now we have a file located at ~/bash/updateall

3) I created a file in my home directory called ".bash_aliases" (without quotes)
4) Inside this .bash_aliases I wrote this:
```
alias apt5='sudo sh ~/bash/updateall'
```5) I restarted bash by logging out and re-logging in.

thats it! now, no matter where I am in my command prompt, I type ```
apt5
``` and my computer will run an apt-get check, apt-get update, apt-get dist-upgrade, apt-get autoclean, and apt-get autoremove.

This has saved me countless typing and I hope it can help a lot of other people here that use apt-get instead of the normal update-manager to install updates.

enjoy!

---

### Post by brunovecchi on 2008-10-23
Nice! I would append '&&' between commands, so that the next one is only executed if the preceding one succeeds.
Let's say your internet connection is down, then the first command fails and then it executes the second one that also needs a connection, and it will obviously fail too.
It's a minor thing, but it makes your otherwise pretty neat script more elegant.

---

### Post by ThaRabbit on 2008-10-23
> **brunovecchi said:**
> Nice! I would append '&&' between commands, so that the next one is only executed if the preceding one succeeds.
Let's say your internet connection is down, then the first command fails and then it executes the second one that also needs a connection, and it will obviously fail too.
It's a minor thing, but it makes your otherwise pretty neat script more elegant.

additionally, this commando:
```
sudo apt-get clean
```

Will delete the local cache of packages downloaded via synaptic or other methods.

note that you can also configure this in synaptic. Settings -> Preferences -> Files :)

---

### Post by semitone36 on 2008-10-23
Could you explain what each of those commands do?
<- terminal noob

---

### Post by kerry_s on 2008-10-23
i just use alias's

```
alias s='apt-cache search'
alias i='sudo apt-get install'
alias r='sudo apt-get --purge remove'
alias upd='sudo apt-get update;sudo apt-get dist-upgrade;sudo apt-get clean;sudo orphaner'

```

example:

s editor = search editor
i geany = installs geany
r geany = removes
upd = updates and shows upgrades, then cleans


yours:
**alias all4='sudo apt-get update;sudo apt-get dist-upgrade;sudo apt-get autoclean;sudo apt-get autoremove'**

---

### Post by steveydoteu on 2008-10-23
Expanding on this, taking updating out of the equation for the time being, I feel that a script to keep the packages in good order would be useful. I will share mine as follows:

```
#!/bin/bash
# keep that package list nice and healthy
# script to check nothing is broken and clean out all the fluff
# www.stevey.eu

apt-get check &&

apt-get autoremove &&

apt-get autoclean &&

apt-get clean
  

```This way we are ensuring everything is in good working order and there is nothing left behind to cause possible issues prior to any attempts at syncing package lists or updating anything on our systems, far safer.

For those not savvy with the terminal and apt-get commands:

**check** will check that you have got no broken packages/dependancies

**autoremove** will remove any packages left behind that were installed previously by something else and are no longer required

**autoclean **will erase any old archive files used from previous installations of packages

**clean **as above but the more recent ones

---

### Post by steveydoteu on 2008-10-23
> **kerry_s said:**
> i just use alias's

```
alias s='apt-cache search'
alias i='sudo apt-get install'
alias r='sudo apt-get --purge remove'
alias upd='sudo apt-get update;sudo apt-get dist-upgrade'
alias old='sudo apt-get clean;sudo orphaner'
```

I have never taken the time to try it out, as I usually use a custom filter within synaptic, but I am presuming *orphaner *is part of deborphan?

Does it just work automagically without any prompts removing all the orphaned packages?

---

### Post by kerry_s on 2008-10-23
> **steveydoteu said:**
> I have never taken the time to try it out, as I usually use a custom filter within synaptic, but I am presuming *orphaner *is part of deborphan?

Does it just work automagically without any prompts removing all the orphaned packages?

no, everything on mine asks first, you would have to use the " -y, --yes, --assume-yes" if you want that.

for example, after dist-upgrade, if there's upgrades it stops with the "yes,no" question, then continues.

";" makes it only move on after the other is completed.

yes, orphaner is deborphan, you might want to take that out for ubuntu. i'm using etch.

---

### Post by steveydoteu on 2008-10-23
> **semitone36 said:**
> Could you explain what each of those commands do?
<- terminal noob

[http://wiki.linuxhelp.net/index.php/Apt-get_Guide](http://wiki.linuxhelp.net/index.php/Apt-get_Guide)

---

### Post by bodhi.zazen on 2008-10-23
Rather the writing a script you can define a function in .bashrc

update () {
command1 && command2 && command3 && command4
}

---

### Post by tgalati4 on 2008-10-23
Great script.  What's missing is some logic to check for the following:

The Linux Mint folks use an Update protocol that hides updates of the linux kernel and xorg (video) because they tend to break things like boot up.

A blind update of the kernel and video system can lead to a broken system on the next reboot.  Because this reboot may occur many days later (for a server, for instance) the  cause of the breakage is not obvious.

There should at least be a warning if the package contains "kernel" or "xorg" and perhaps other keywords to let the user know that these updates can cause breakage.

For instance, every time the kernel is updated, GRUB is rerun and on some customized systems this breaks because of the mixture of SATA and IDE drives or a custom RAID configuration.  The fixes are usually simple, but you are still staring at busybox scratching your head.

Linux Mint Update uses a smart approach by rating updates using a 1-5 scale and hiding the 4 and 5 Risk Level from the casual user.  You can always change it in preferences, but at least the casual user is less likely to break their system with a simple update.

---

### Post by bash on 2008-10-23
> **kerry_s said:**
> i just use alias's

```
alias s='apt-cache search'
alias i='sudo apt-get install'
alias r='sudo apt-get --purge remove'
alias upd='sudo apt-get update;sudo apt-get dist-upgrade;sudo apt-get clean;sudo orphaner'

```

example:

s editor = search editor
i geany = installs geany
r geany = removes
upd = updates and shows upgrades, then cleans


yours:
**alias all4='sudo apt-get update;sudo apt-get dist-upgrade;sudo apt-get autoclean;sudo apt-get autoremove'**

Looks quite neat to save some time always typing it out. Where do I have to specify the aliases? Just in .bashrc?

---

### Post by steveydoteu on 2008-10-23
> **bash said:**
> Looks quite neat to save some time always typing it out. Where do I have to specify the aliases? Just in .bashrc?

> **bash said:**
> Looks quite neat to save some time always typing it out. Where do I have to specify the aliases? Just in .bashrc?

No, you need a .bash_aliases file in your ~/ directory.

Then define an alias as follows:

```
 alias myalias='bash command(s)'
```

---

### Post by qpieus on 2008-10-23
You can put aliases in .bashrc (you don't absolutely need a .bash_aliases file), although I like using the .bash_aliases file so I don't have to hunt thru my .bashrc file to find the aliases section.

---

### Post by kerry_s on 2008-10-23
> **bash said:**
> Looks quite neat to save some time always typing it out. Where do I have to specify the aliases? Just in .bashrc?

i just use ~/.bashrc, no need to get complicated, i just put it at the top. see pic

---

### Post by Saint Angeles on 2008-10-24
> **ThaRabbit said:**
> additionally, this commando:
```
sudo apt-get clean
```Will delete the local cache of packages downloaded via synaptic or other methods.

note that you can also configure this in synaptic. Settings -> Preferences -> Files :)
whats the difference between clean and autoclean?

also i'm going to add && to the end of the top three lines as suggested above. i'm going to edit the post accordingly...

---

### Post by Saint Angeles on 2008-10-24
OK i've added 'apt-get check' to the list.

but now its 5 commands and the title says 4 commands! HAHA.

is it possible to change the title?

---

### Post by kerry_s on 2008-10-24
> **Saint Angeles said:**
> whats the difference between clean and autoclean?

also i'm going to add && to the end of the top three lines as suggested above. i'm going to edit the post accordingly...

autoclean only cleans whats no longer available, so it doesn't need to be downloaded again if you had to reinstall a program. (waste of space)

clean clears everything out so if you were to reinstall a program it would have to be downloaded again.

---

### Post by Saint Angeles on 2008-10-24
> **kerry_s said:**
> autoclean only cleans whats no longer available, so it doesn't need to be downloaded again if you had to reinstall a program. (waste of space)

clean clears everything out so if you were to reinstall a program it would have to be downloaded again.

so should i replace the autoclean command with clean?

---

### Post by ultratot on 2008-10-24
This seems pretty straightforward, right? That's why its so frustrating that I can't get it to work. I did everything and restarted my computer and all and when I type apt5 into the terminal it tells me "bash: apt5: command not found" (without the quotes of course). I suspect its nothing wrong with the script itself because of it would say something other than command not found if it was. This worries me further because this is the first alias I've tried to do and if I can't get it to work, i doubt i'll be able to make any work later on. 

Any thoughts on why this might be? Any insight is appreciated.

---

### Post by Saint Angeles on 2008-10-25
> **ultratot said:**
> This seems pretty straightforward, right? That's why its so frustrating that I can't get it to work. I did everything and restarted my computer and all and when I type apt5 into the terminal it tells me "bash: apt5: command not found" (without the quotes of course). I suspect its nothing wrong with the script itself because of it would say something other than command not found if it was. This worries me further because this is the first alias I've tried to do and if I can't get it to work, i doubt i'll be able to make any work later on. 

Any thoughts on why this might be? Any insight is appreciated.
yeah... this is really strange. I've tried everything I know to help you on the phone.

does anybody here have any ideas?

---

### Post by kerry_s on 2008-10-25
> **ultratot said:**
> This seems pretty straightforward, right? That's why its so frustrating that I can't get it to work. I did everything and restarted my computer and all and when I type apt5 into the terminal it tells me "bash: apt5: command not found" (without the quotes of course). I suspect its nothing wrong with the script itself because of it would say something other than command not found if it was. This worries me further because this is the first alias I've tried to do and if I can't get it to work, i doubt i'll be able to make any work later on. 

Any thoughts on why this might be? Any insight is appreciated.

if your using the script method, you need to make that executable. 

the ~/.bashrc method you just put in in there it works right away.

if you show us exactly what you have, we can see if the command is okay.

---

### Post by ultratot on 2008-10-25
Ok, I now see what the problem was. For whatever reason, maybe someone else out there knows, there were a few lines commented out in the .bashrc file in the home (~) folder. these were the lines that gave bash the instructions to look at .bash_aliases for any custom-made bash commands. So, if anyone else has this same problem i described in my previous post, look at the .bashrc and make sure the following code isn't commented out with # signs. 

```
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```

Thanks though to kerry_s.

---

### Post by kerry_s on 2008-10-25
> **ultratot said:**
> Ok, I now see what the problem was. For whatever reason, maybe someone else out there knows, there were a few lines commented out in the .bashrc file in the home (~) folder. these were the lines that gave bash the instructions to look at .bash_aliases for any custom-made bash commands. So, if anyone else has this same problem i described in my previous post, look at the .bashrc and make sure the following code isn't commented out with # signs. 

```
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```

Thanks though to kerry_s.


no, thank you i never even noticed that section. but than again i'm in and out of there so fast cause i already know how i want it. :lolflag:
i don't use enough alias's to warrant using a extra file, but i'll chalk that up to another thing learned. :)

---

### Post by steveydoteu on 2008-11-01
You have still managed to overlook the fact that **clean **and **autoclean **are two entirely different switches.

```
Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove and purge packages
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
  [B] [COLOR=RoyalBlue]clean - Erase downloaded archive files[/COLOR]
  [COLOR=YellowGreen] autoclean - Erase_ old _downloaded archive files[/COLOR][/B]
   check - Verify that there are no broken dependencies

```The substantial difference being the later removes what apt deems to be 'old', where as the earlier will remove those recently created.

It is also worthwhile adding a purge switch to the autoremove line, as it will also then take with it any old configuration files.
 ```
autoremove --purge
```

---

### Post by Saint Angeles on 2008-11-01
> **steveydoteu said:**
> You have still managed to overlook the fact that **clean **and **autoclean **are two entirely different switches.

```
Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove and purge packages
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
  [B] [COLOR=RoyalBlue]clean - Erase downloaded archive files[/COLOR]
  [COLOR=YellowGreen] autoclean - Erase_ old _downloaded archive files[/COLOR][/B]
   check - Verify that there are no broken dependencies

```The substantial difference being the later removes what apt deems to be 'old', where as the earlier will remove those recently created.

It is also worthwhile adding a purge switch to the autoremove line, as it will also then take with it any old configuration files.
 ```
autoremove --purge
```

so why is having autoclean in my script a bad thing? its a good thing... right?

and sure... i'll add --purge to the autoremove line.

---

### Post by bapoumba on 2008-11-01
I've removed the last 3 useless posts - Please remember we can very well disagree, but always politely. Thanks.

---

### Post by steveydoteu on 2008-11-01
> **bapoumba said:**
> I've removed the last 3 useless posts - Please remember we can very well disagree, but always politely. Thanks.

Hmm sounds like not respecting other users there.

As I was trying to say, validly.

My posts have been informative, seeing as you had given the impression of not knowing an awful lot about what you were doing to begin with, especially with the number of questions you were asking. Criticism is a key to success, and mine has all been constructive. If you cannot cope with that, then I suggest not publishing your scripts on the forums.

I notice you have also over looked the suggestion to add && to the end of each line, as to stop the script sailing on even if the prior line fails.

My advice to any readers would be to create your own script from scratch, using suggestions such as the double ampersand and not using dist-upgrade in the middle of it all to save on possible breakages, and so forth.

---

### Post by Saint Angeles on 2008-11-01
> **steveydoteu said:**
> Hmm sounds like not respecting other users there.

As I was trying to say, validly.

My posts have been informative, seeing as you had given the impression of not knowing an awful lot about what you were doing to begin with, especially with the number of questions you were asking. Criticism is a key to success, and mine has all been constructive. If you cannot cope with that, then I suggest not publishing your scripts on the forums.

I notice you have also over looked the suggestion to add && to the end of each line, as to stop the script sailing on even if the prior line fails.

My advice to any readers would be to create your own script from scratch, using suggestions such as the double ampersand and not using dist-upgrade in the middle of it all to save on possible breakages, and so forth.

what? i added && to the end of everyline!! and i included a warning about possible breakages resulting in upgrading the kernel and xorg. you keep saying i "overlooked" stuff when i didn't at all. can a mod please help prevent this guy from trolling all over this thread?

and dist upgrade is the most important part of this script.

why do you keep saying rude things? i can post whatever i want on the forums. i'm sorry if you don't think i'm smart enough to write bash scripts and im sorry you inferred that i don't know anything about apt-get... but several people (friends of mine included) have seen this script as beneficial.

---

### Post by Saint Angeles on 2008-11-01
> **steveydoteu said:**
> My posts have been informative, seeing as you had given the impression of not knowing an awful lot about what you were doing to begin with, especially with the number of questions you were asking.
with your logic, Socrates didn't know anything. theres a certain wisdom and humility that comes from asking questions.

---

### Post by steveydoteu on 2008-11-01
I am not doubting any benefits of such a script, I have just made suggestions that may well improve it. At the time of writing you *had *overlooked the information regarding clean and the double ampersand, I felt it needed to be suggested. Interesting reading regarding the dist-upgrade vs upgrade argument here: [http://www.linuxquestions.org/questions/fedora-35/apt-get-question-dist-upgrade-vs-upgrade-219920/](http://www.linuxquestions.org/questions/fedora-35/apt-get-question-dist-upgrade-vs-upgrade-219920/)

Granted the warning is now there, but being as not everyone will read the entire thread it could still benefit to mention what the commands do, or even simply how to access the help via apt-get -h. This link is also useful reading from a documentation point of view, [http://wiki.linuxhelp.net/index.php/Apt-get_Guide](http://wiki.linuxhelp.net/index.php/Apt-get_Guide)

I never once suggested you knew nothing about apt, I actually just happened to mention that it is still only a front end for dpkg. [http://en.wikipedia.org/wiki/Dpkg](http://en.wikipedia.org/wiki/Dpkg)

This is not trolling in the slightest, I am offering my suggestions and opinions. You had given the **impression** of not knowing an awful lot about what you were doing to begin with, especially with the number of questions you were asking. I have not doubted the vast benefits of asking questions.

I did not realize that offering my opinion and suggestions was rude. You indeed are perfectly entitled to post whatever you choose, but on that note so is anyone else. I apologise if any offense has been caused.

---

### Post by Saint Angeles on 2008-11-01
> **steveydoteu said:**
> I am not doubting any benefits of such a script, I have just made suggestions that may well improve it. At the time of writing you *had *overlooked the information regarding clean and the double ampersand, I felt it needed to be suggested. Interesting reading regarding the dist-upgrade vs upgrade argument here: [http://www.linuxquestions.org/questions/fedora-35/apt-get-question-dist-upgrade-vs-upgrade-219920/](http://www.linuxquestions.org/questions/fedora-35/apt-get-question-dist-upgrade-vs-upgrade-219920/)

Granted the warning is now there, but being as not everyone will read the entire thread it could still benefit to mention what the commands do, or even simply how to access the help via apt-get -h. This link is also useful reading from a documentation point of view, [http://wiki.linuxhelp.net/index.php/Apt-get_Guide](http://wiki.linuxhelp.net/index.php/Apt-get_Guide)

I never once suggested you knew nothing about apt, I actually just happened to mention that it is still only a front end for dpkg. [http://en.wikipedia.org/wiki/Dpkg](http://en.wikipedia.org/wiki/Dpkg)

This is not trolling in the slightest, I am offering my suggestions and opinions. You had given the **impression** of not knowing an awful lot about what you were doing to begin with, especially with the number of questions you were asking. I have not doubted the vast benefits of asking questions.

I did not realize that offering my opinion and suggestions was rude. You indeed are perfectly entitled to post whatever you choose, but on that note so is anyone else. I apologise if any offense has been caused.

the second somebody posted information about the &&, i had added it to the script... i even added your suggestion about --purge the SECOND i saw it.

also, the second i saw concern about what dist upgrade might do, i added a warning.

it was the way you were saying your suggestions... that i "managed to overlook" things, like i was trying to overlook them on purpose. and i hadn't overlooked ANYTHING. i asked about the difference of clean and autoclean instead of simply telling me what the difference was, you said "you still managed to overlook the difference..."

how did i overlook it if you were the first one to answer my question?

also, i've been using ubuntu since feisty and i dont use update manager. i use apt-get dist-upgrade and i type it many times a day. ive never once had a problem... a lot of people like to update their kernel. a lot of people are like me and use dist-upgrade with no problems.

i didnt want to use clean because i dont want to erase EVERY package file, just the ones that arent needed... thats why i went with autoclean. my script works well for those of us that understand what it is we are doing. and besides adding a warning to the OP (which i did as SOON as it was suggested) what more can i do to prevent somebody from doing something bad with this script?

theres a difference between "here is the difference between clean and autoclean..." and "you've managed to overlook the fact that clean and autoclean are different..."

EDIT: i just re-read the thread. i didn't realize you were the one helping me from the beginning. i think there was a miscommunication somewhere... probably on my part. i've been super stressed out lately and i just recently got another webmaster job thats taken some of my focus.

truce?

---


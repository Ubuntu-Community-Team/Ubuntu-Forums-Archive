---
title: "What's up with Medibuntu in Synaptic?"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by the.scarecrow on 2009-01-21
I just installed Intrepid 8.10 on a spare hard drive to give it a test run. I want to install Skype so I followed the current Medibuntu installation instructions to include Medibuntu in the repositories. I have done this before in Hardy and could then use Synaptic to install the Apps I wanted.

The Medibuntu installation appeared to go OK.

However, in Synaptic none of the Medibuntu apps seem to be there. No Skype or Googleearth for example. This is the same in Add/Remove with "All available applications" selected in the show box.

So what's wrong? why can I no longer use Synaptic to install Medibuntu Apps?

---

### Post by awam66 on 2009-01-21
Have you checked that they are ticked in the System>administration>software sources. look at the "Third Party" tab and you should see the medibuntu repositories. Make sure they are ticked the do a reload and they should appear in synaptic.

---

### Post by OrangeCrate on 2009-01-21
After you installed the repositories, did you install the GPG key?

See here for instructions:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by oldos2er on 2009-01-21
Did you forget to click 'Reload'?

---

### Post by the.scarecrow on 2009-01-21
> **awam66 said:**
> Have you checked that they are ticked in the System>administration>software sources. look at the "Third Party" tab and you should see the medibuntu repositories. Make sure they are ticked the do a reload and they should appear in synaptic.

Yes Medibuntu is ticked under the "Third Party" tab and I just reloaded Synaptic but Skype and Googleearth are still not available.

Thanks for your help but that's not the problem.

---

### Post by the.scarecrow on 2009-01-21
> **OrangeCrate said:**
> After you installed the repositories, did you install the GPG key?

See here for instructions:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Yes I did install the GPG key, I did this first:

> Ubuntu 8.10 "Intrepid Ibex":

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

Then this:

> Then, add the GPG Key:

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Thanks for your help but is still is not working.

---

### Post by the.scarecrow on 2009-01-21
> **oldos2er said:**
> Did you forget to click 'Reload'?

No I didn't forget to reload Synaptic.

---

### Post by taurus on 2009-01-21
Post the output of this command from a terminal.

```
ls -la /etc/apt/sources.list.d
```

---

### Post by the.scarecrow on 2009-01-21
> **taurus said:**
> Post the output of this command from a terminal.

```
ls -la /etc/apt/sources.list.d
```

This is what I get:

> laptop:~$ ls -la /etc/apt/sources.list.d
total 12
drwxr-xr-x 2 root root 4096 2009-01-20 23:10 .
drwxr-xr-x 4 root root 4096 2009-01-21 21:17 ..
-rw-r--r-- 1 root root  230 2008-08-18 22:13 medibuntu.list
laptop:~$ 


Hope that helps.

---

### Post by taurus on 2009-01-21
Can you post the content of that file?

```
cat /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by the.scarecrow on 2009-01-21
> **taurus said:**
> Can you post the content of that file?

```
cat /etc/apt/sources.list.d/medibuntu.list
```

I get:

> laptop:~$ cat /etc/apt/sources.list.d/medibuntu.list
## Medibuntu - Ubuntu 8.10 "intrepid ibex"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
laptop:~$ 


Thanks for your help.

---

### Post by taurus on 2009-01-21
What happens when you run these commands from a terminal?

```
sudo apt-get update
sudo apt-get install googleearth
```

---

### Post by the.scarecrow on 2009-01-21
I don't want to install Googleearth but I can do Skype. before I do that I checked back to see what I did when I added Medibuntu to Hardy. It was 

> sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

then

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

compared to now for Intrepid:

> sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

then

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Note the two first lines are slightly different e.g.
/hardy.list -O /etc/apt/sources.list.d/
/intrepid.list --output-document=/etc/apt/sources.list.d/

Hardy works, do you think this has anything to do with it?

---

### Post by taurus on 2009-01-21
Your /etc/apt/sources.list.d/medibuntu.list looks fine to me.  Are you running intrepid or hardy?  If you want to install skype, use the lower case letter s, not capital S.

```
sudo apt-get update
sudo apt-get install skype
```

---

### Post by the.scarecrow on 2009-01-21
> **taurus said:**
> Your /etc/apt/sources.list.d/medibuntu.list looks fine to me.  Are you running intrepid or hardy?  If you want to install skype, use the lower case letter s, not capital S.

```
sudo apt-get update
sudo apt-get install skype
```

OK skype installed OK I got the message to enter

apt-get autoremove

to remove some temporary files, I don't know what to do about that. Also the sound isn't working on skype although it is working in all the other apps I have installed.

This does not solve why I can't install using Synaptic like I do in Hardy. I have two hard disks, my normal disk is just Hardy and that works great. I have this junk disk with XP Pro on it so I added Intrepid to test it out prior to using Intrepid on my main disk in place of Hardy. Hope that makes sense.

Thanks

---

### Post by mc4man on 2009-01-21
> This does not solve why I can't install using Synaptic like I do in Hardy
If your using the quick search box and typing in, then many times you'll get nothing or not what your looking for. If you use the search pop up it will work fine (as long as nothing is entered in the quick search
The quick search is best for pasting in.

---

### Post by the.scarecrow on 2009-01-22
> **mc4man said:**
> If your using the quick search box and typing in, then many times you'll get nothing or not what your looking for. If you use the search pop up it will work fine (as long as nothing is entered in the quick search
The quick search is best for pasting in.

BINGO! Thats It, you got it. By habit in Hardy I always havw used the Quick Search box. Using the search pop up box it finds all the missing Medibuntu Apps heh! heh! just installed the W32codecs from Synaptic, no problems.

I've even fixed Skype by putting pulse in all three sound option boxes.

Thanks yoall you guys are diamonds so now I can migrate to Intrepid 100%.

---


---
title: "completely deleting files"
date: 2008-08-23
forum: General Help
---

### Post by jesse c on 2008-08-23
I have been having problems with google earth.I had(have) GE4.2 and GE4.3 both loaded on my desktop.They both used to work,now they both have some graphic bug.I decided to remove both copies ,going for clean install.I went into synaptic and everything with google earth title i marked for "complete removal" now there is nothing GE checked off in synaptic but when i go to Applications/Internet there is still a GE icon that still comes up and still comes up with the bad graphics problem.How do i remove all old GE files so i can re load and test see if fresh install fixes problems?
thanks JESSE C

---

### Post by tommcd on 2008-08-23
You could try from terminal
```
sudo apt-get remove --purge googleearth
```
See if that does it.
So you are saying that even since you marked them for complete removal in synaptic you can still run them from applications > internet > google earth, is that right? Does synaptic now show them as installed or uninstalled? Check for both versions in synaptic to see if they were both purged. Did you originally install them from synaptic, or download them from google?
Or you could just use synaptic to install the new version over the old, but try "apt-get remove --purge" first.
And you should probably only have 1 version of google earth instaled at a time from now on.

---

### Post by jesse c on 2008-08-24
TOMMCD i probably had loaded them both ways,the 4.2 from synaptic and the new 4.3 from the internet,before it was supported by synaptic.I tried the purge code and it says there is no GE to purge yet it is still on my applications/internet listing

---

### Post by tommcd on 2008-08-26
So you installed GE 4.2 from synaptic; and then you downloaded GE 4.3 directly from google, is that right?
Then you uninstalled GE 4.2 from synaptic, but you can still launch GE 4.3 from applications > internet. Is this right? If so, then how did you install the GE from google? If you installed GE with "sudo ./googleearth" it probably went to /usr/local/googleearth, or /opt/googleearth. Look in /usr/local or /opt for a googleearth directory. If you have one you can remove it with "sudo rm -r /usr/local/googleearth" or "sudo rm -r /opt/googleearth". There will also be a symlink in /usr/bin that you can remove with "sudo rm /usr/bin/googleearth".
This ONLY applies if you installed GE from google with sudo.

If you installed GE from google by just running ./googleearth, then it will be located in your home directory and you can just delete that. There may also be a hidden directory called .googleearth in your home directory that you can remove also.

---

### Post by jesse c on 2008-08-26
TOMMCD   I dont know code,even though i bought two books when igot into Ubuntu -Linux for Dummies and Ubuntu for Non Geeks. That being said i would have used synaptic ,which i went back and did the 'completely remove,thing for every GE available.As far as web i would have gone to GE page and just clicked the 'download now' button,no sudo involved there.Since im still a step below a non geek dummy in linux commands can you give me some 'copy/paste' code that i can use to find then remove? I did get out the book and did a ls command that brought up three GE entries (one said 'Safari' which i dont have installed) but i dont know what to do with that info,i was just trying some crude book lernin practice
thanks JESSE C

---

### Post by tommcd on 2008-08-28
You will need to answer this question, which I asked you in my last post:
> How exactly did you install the google earth that you got from google??
When you answer that question I will have a better idea where it went, so I can tell you how to remove it. To install it you had to have run either "sh googleearth" or "sudo sh googleearth". If you just ran sh googleearth then just delete the googleearth folder in your home directory.
If you ran "sudo sh googleearth" then (like I said in my last post) it either went to /opt/google-earth or /usr/local/google-earth.
Look for a google-earth directory in /opt and /usr/local. If it went to /opt run
```
sudo rm -r /opt/google-earth
```
if it went to /usr/local run
```
sudo rm -r /usr/local/google-earth
```
There will also be a symlink launcher in /usr/loca/bin (Last time I incorrectly said it would be in /usr/bin. I was not at my linux box at the time so I couldn't check; but it is indeed in /usr/local/bin.
To remove that run ```
sudo rm /usr/loca/bin/google-earth
```
If the launcher still remains under applications > internet, to remove it just right click on the applications menu at the top panel and select "edit menus", go to "internet" and uncheck the entry for google-earth if it's there.

So again, how did you install google earth that you got from google??

---

### Post by jesse c on 2008-08-31
TOMMCD thanks for sticking with me but i thought i made it kinda clear that i have no clue as to where or how GE was installed. This is my first computer and since i dont know Windows i felt learning Ubuntu would make me feel less stupid,so i dont know how to install downloaded files by terminal and only know synaptic method or just clicking 'download here' on a web page and hoping for success (very seldom happens-thats why i bought books) So is there any problem copy/paste each of your command codes and see what deletes? If the file isnt in one place it will just say "file not found" or some such,wont it?Oh by the way i fixed GE by some private GE forum site the official GE Community Forums site was so unhelpful i couldnt even figure out how to ask questions,everything is a 'read only' forum. But i still want to learn how i could have deleted all GE files and started from fresh install,it would have fixed the problem faster than the work around.

---


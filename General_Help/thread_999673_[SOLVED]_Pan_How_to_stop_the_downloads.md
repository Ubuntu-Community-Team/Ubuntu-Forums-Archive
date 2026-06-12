---
title: "[SOLVED] Pan: How to stop the downloads"
date: 2008-12-02
forum: General Help
---

### Post by GuiGuy on 2008-12-02
A little OT: I installed Pan which seemed a competent binary downloader. But now, when I start it, the thing is insisting in downloading ALL of the binaries in a huge newsgroup. We're talking  terrabytes, I think.

How do I stop it? In other words, how do I abort the downloads? 

Thanks

---

### Post by nhasian on 2008-12-05
I highly recommend LottaNZB. its a front end for HellaNZB and very easy to use. Once its installed you just click on a .nzb file and it automatically retrieves the files, error checks them, downloads parity files if necessary, uncompresses it and moves it to your done folder. You can also just drag and drop .nzb files to the queue directory. 

To install LottaNZB:

```
sudo apt-get install lottanzb
```

this will also install hellanzb and its dependencies.

---

### Post by GuiGuy on 2008-12-05
> **nhasian said:**
> 
To install LottaNZB:

```
sudo apt-get install lottanzb
```

this will also install hellanzb and its dependencies.

Thanks for that. I usually use hellanzb but sometimes I just want to download a small binary and thought something like Pan would be adequate for that. 

But yea, I like hellanzb a lot so will try lottanzb

Thanks again

---

### Post by GuiGuy on 2008-12-05
> **nhasian said:**
> 
To install LottaNZB:

```
sudo apt-get install lottanzb
```

this will also install hellanzb and its dependencies.

For the benefit of others, the above didn't work for me. There is no lottanzb in the default repository. 

However, you can [download and install a ubuntu package here]("http://www.lottanzb.org/downloads").

---

### Post by oldos2er on 2008-12-05
Under Edit, Preferences, Behavior, Groups, uncheck both the 'Get New Headers' options.

---

### Post by GuiGuy on 2008-12-05
> **oldos2er said:**
> Under Edit, Preferences, Behavior, Groups, uncheck both the 'Get New Headers' options.

No, that didn't work. What happened was that I had accidentally selected everything in a group for download. The downloading starts immediately once I run Pan. Your suggestion has no effect on that. 

I suspect it is a bug/ omission. I have contacted the Pan team.

Thanks

---

### Post by nhasian on 2008-12-06
weird.  i did:

```
apt-cache search lottanzb
```

and i found it there.  also in synaptic package manager.  i guess I must have added the .deb file manually when i first started using it.

> **GuiGuy said:**
> For the benefit of others, the above didn't work for me. There is no lottanzb in the default repository. 

However, you can [download and install a ubuntu package here]("http://www.lottanzb.org/downloads").

---


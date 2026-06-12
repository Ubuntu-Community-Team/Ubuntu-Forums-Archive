---
title: "Brand new DeskJet 3632 was printing in color yesterday, today no more"
date: 2016-12-19
forum: Hardware
---

### Post by juntjoo2 on 2016-12-19
Title basically sums it up. It was printing color just fine the other day. Bought the printer a few days ago. Checked all the settings in device manager.  Tried with test page and usual files. Also, for example if I print a page of colored text it comes out a poor quality grey. I guess that's what a color print looks like when it's not actually drawing from the color ink.  If I restart my laptop in Windows this doesn't happen so it's not hardware. Any ideas?

---

### Post by juntjoo2 on 2017-01-07
Anyone have any ideas? Still only printing black and white and very slowly.

---

### Post by oldfred on 2017-01-07
What version of HPLIP are you using.
Did you install the usually somewhat older version from Ubuntu repository or directly from HP?

I typically have had to install from HP as new printer needed newer HPLIP.
HP's newest On this website you can download the HPLIP software which supports 2,211 HP printers on nearly any Linux distribution available today.
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

### Post by juntjoo2 on 2017-01-07
> **oldfred said:**
> What version of HPLIP are you using.
Did you install the usually somewhat older version from Ubuntu repository or directly from HP?

I typically have had to install from HP as new printer needed newer HPLIP.
HP's newest On this website you can download the HPLIP software which supports 2,211 HP printers on nearly any Linux distribution available today.
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)


Thanks.That-is-where-recently-went-to-reinstall-my-drivers.-strange-suddenly-can't-use-space-bar-in-here.-should-I-have-uninstalled-them-first-before-reinstalling-them?-if-so-I-don't-know-how-to-uninstall-drivers-on-this-system.

---

### Post by oldfred on 2017-01-07
HP seems to be ok on uninstalling old version when installing new version. 
Have not installed from repository and then from HP, so do not know if difference matters.
You should be able to just uninstall from command line or from synaptic. I have never used Software Center, it may be there also?

       sudo apt-get install synaptic 
Search on hplip

Or command line
sudo apt-get purge hplip

Not sure what support/dependencies are also installed.
I know when downloading from HP it expects some support software to already be installed.

---

### Post by juntjoo2 on 2017-01-07
in synaptic all I have installed is "openprinting-ppds" and then there are a lot of others under "hplip".  Should I do anything with them? Should any of these already be installed?

---

### Post by oldfred on 2017-01-07
I showed hplip installed and several other related files hplip-data & hplip-gui.
I thought I used the HP site with this computer, but maybe driver in repository was new enough.

---

### Post by juntjoo2 on 2017-01-09
anyone else have any ideas?  I uninstalled the drivers per [http://hplipopensource.com/node/188](http://hplipopensource.com/node/188) instructions but after boot up it's still there at the top of the screen and printing in black and white?  Anyone know where else to search for help?  I've already started a thread at linuxquestions.org but not getting any new info.

so I solved it, how, idk exactly, but as shown in the pic I installed all these instances of hplip, where the only one installed before was the first one.  Were these supposed to be installed before, idk.  I just took a shot in the dark and got lucky. Anyone know what happened and why it works now but didn't before please enlighten me as I hate solving problems ignorantly as it means should it occur again I won't have the knowledge to fix it again necessarily.  

[IMG]http://img-cdn.filefactory.com/embed/xl/4jz4sf3y7iv3.png[/IMG]

---


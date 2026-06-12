---
title: "Is there any means to downgrade a package?"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by Pidgin on 2008-12-20
Recently I added the compiz repository on Launchpad. And Synaptic found a new version of compiz and upgraded the package and some other related packages. Now I do not like the new version and want to return to the old version in the official repository. But it seems impossible for apt-get or Synaptic to do a downgrade.
I have considered removing the compiz repository and the compiz package and then reinstalling. But unfortunately removing the compiz package will result in removing nearly the whole system.
Would anyone please help me?

---

### Post by ShirishAg75 on 2008-12-20
Pidgin, 
        Here's what you could do. Either see your apt log and carefully note down the version number from which you upgraded and install that version or go to [http://launchpad.net/ubuntu](http://launchpad.net/ubuntu) and see [https://launchpad.net/ubuntu/+source/compiz](https://launchpad.net/ubuntu/+source/compiz)

Let's just say its Intrepid you are using (You haven't told which version of the distribution you are using) then do 

```
$ sudo apt-get install compiz=1:0.7.8-0ubuntu4.1
``` 

or 

```
$ sudo apt-get install compiz=1:0.7.8-0ubuntu4
```

depending on whether you are using the updates repository or not. 

The first one is when your updates repository is on and the second is without. 

It will pull in the required stuff and downgrade also the dependencies if need be. 

Now remove the third-party repository either through System > Administration > Software Sources or using your favorite editor in /etc/apt/sources.list and remove or comment out that repository so it doesn't try to update it again the next time you do an update upgrade procedure. 

Hope this helps.

---

### Post by Pidgin on 2008-12-20
> **ShirishAg75 said:**
> Pidgin, 
        Here's what you could do. Either see your apt log and carefully note down the version number from which you upgraded and install that version or go to [http://launchpad.net/ubuntu](http://launchpad.net/ubuntu) and see [https://launchpad.net/ubuntu/+source/compiz](https://launchpad.net/ubuntu/+source/compiz)

Let's just say its Intrepid you are using (You haven't told which version of the distribution you are using) then do 

```
$ sudo apt-get install compiz=1:0.7.8-0ubuntu4.1
``` 

or 

```
$ sudo apt-get install compiz=1:0.7.8-0ubuntu4
```

depending on whether you are using the updates repository or not. 

The first one is when your updates repository is on and the second is without. 

It will pull in the required stuff and downgrade also the dependencies if need be. 

Now remove the third-party repository either through System > Administration > Software Sources or using your favorite editor in /etc/apt/sources.list and remove or comment out that repository so it doesn't try to update it again the next time you do an update upgrade procedure. 

Hope this helps.
Thank you!
But I am not very clear about the difference. What does "using the updates repository or not" mean? I have removed the repository on Launchpad.

---


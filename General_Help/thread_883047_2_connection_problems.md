---
title: "2 connection problems"
date: 2008-08-07
forum: General Help
---

### Post by carl.alv on 2008-08-07
Hi everyone!

I make this post because I have two connection problems in Hardy which may (or may not) be related.

*The fist problem is that the automatic update manager does not work. A warning sign appears and tells me that I must check manually for updates, and once I try that I tells me
```

Failed to fetch http://packages.dfreer.org/dists/feisty/main/binary-amd64/Packages.gz  302 Found
Some index files failed to download, they have been ignored, or old ones used instead.

```
and it does not load any package.

*The second problem is with amsn. When I try to login it stays in the "logging in..." phase forever.

I am grateful for any help.

---

### Post by plucky on 2008-08-07
> **carl.alv said:**
> Hi everyone!

I make this post because I have two connection problems in Hardy which may (or may not) be related.

*The fist problem is that the automatic update manager does not work. A warning sign appears and tells me that I must check manually for updates, and once I try that I tells me
```

Failed to fetch http://packages.dfreer.org/dists/[color=red]feisty[/color]/main/binary-amd64/Packages.gz  302 Found
Some index files failed to download, they have been ignored, or old ones used instead.

```
and it does not load any package.

*The second problem is with amsn. When I try to login it stays in the "logging in..." phase forever.

I am grateful for any help.

I would change that line as it is for Feisty to Hardy as you are running Hardy,or comment it out of your **/etc/apt/sources.list** file and then run ```
sudo apt-get update
``` to see if you still get a problem.

I am not sure about the second problem


Good Luck

---

### Post by carl.alv on 2008-08-07
Thank you for your answer. I removed the feisty repositories but when I reload them I still get

```

Failed to fetch http://packages.medibuntu.org/dists/hardy/non-free/binary-amd64/Packages.gz  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Failed to fetch http://packages.medibuntu.org/dists/hardy/free/source/Sources.gz  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Failed to fetch http://packages.medibuntu.org/dists/hardy/non-free/source/Sources.gz  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by plucky on 2008-08-07
The Medibuntu repository has been having problems today,got the same response when I installed todays updates.I would just ignore it unless what you want to install is in that repository.

Then you will have to wait.


What was it you wanted to install?

---

### Post by carl.alv on 2008-08-07
I wasn't looking forward to install anything specific, it's just that instead of the normal symbol of the automatic update manager I am getting a warning symbol that states

```

The update information is outdated. This may be caused by network problems. Please update manually by clicking on this icon and then selecting 'check'. 

```

but when I do it the manager is not able to retrieve any package. And my network seems to be working OK except for this pair of problems.

---

### Post by plucky on 2008-08-08
Can you please post the output from a terminal of ```
cat /etc/apt/sources.list
``` and also the output of ```
sudo apt-get update
``` which should give us more information of the problem.


p.s Medibuntu repository seems to be working this morning.


Good Luck

---


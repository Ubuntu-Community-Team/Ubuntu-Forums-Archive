---
title: "New Install - appres missing final new line"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by Zork on 2008-12-24
Hi All,

Thanks for taking any time to help out.

When installing Ubuntu 7.04 (yes, I know EOL, but I have to mirror a current running environment), at 95%, I receive the following dialog box:

```
Error Removing Casper
files list file for package 'appres' is missing from final newline 
```

Some background info. When I first installed Ubuntu, I saw the error message, clicked ok and the install continued. Ubuntu seemed to work fine, but whenever I tried to install a package either using 'sudo apt-get' or 'aptitude download' then 'dpkg -i' (all with correct syntax, I am omitting the package name) I would get the same error message above.

I updated sources.list to insure it found the proper package locations and the commands below work:
sudo apt-get clean
sudo apt-get update

I tried to do an upgrade an it failed as well. Any app I try to install, fails. And Synaptic Package Manager will start, I'll enter password, and then it just quits.

I checked the Live CD using the check CD option when you boot from CD and it reports no errors.

Realizing that clicking through the error was a bad idea, I went back in, deleted the Ubuntu partition and reinstalled. And that's where I am now, this time I am leaving it up at the 95% error message you see above.

Any ideas? I can provide more clarification on a particular point if need be.

Thanks and Merry Christmas!

---

### Post by Zork on 2008-12-24
I should add, I looked at appres.list and all I see is @@@@@@@@@@@@@ in the file for about 4 lines.

Thanks!

---


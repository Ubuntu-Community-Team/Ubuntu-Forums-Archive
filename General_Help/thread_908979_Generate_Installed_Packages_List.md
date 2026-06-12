---
title: "Generate Installed Packages List"
date: 2008-09-03
forum: General Help
---

### Post by ShareBuntu on 2008-09-03
I'm trying to use "dpkg --get-selections > list.log" to generate a list of installed applications for when I do a clean install. Is there any way I could format this list to be on one line with only the package names and spaces in between the names?

I.e., how do I format list.log so I can simply copy/paste the contents into 
"sudo aptitude install "? I don't want to use dselect.

---

### Post by cdtech on 2008-09-03
You would just need to save your packages with:
```
dpkg --get-selections > myselections.txt
```
Then to restore the list just:
```
dpkg --set-selections < myselections.txt
```
Then do:
```
apt-get update
```
To refresh the selections then:
```
apt-get upgrade
```
Hope this helps.......

---

### Post by ShareBuntu on 2008-09-03
Thanks for the reply. I followed the first step, removed a package, added the selections in step two, updated and finally upgraded. However, it simply ignored the removed package - leaving me to assume it won't work. Any ideas?

---

### Post by iaculallad on 2008-09-03
I think the last command to issue after:

```
dpkg --set-selections < myselections.txt
```

would be:

```
dselect
```

But as I had read on your post, you don't like to use it.

---

### Post by ShareBuntu on 2008-09-03
Sorry to double post. Found it: [http://ubuntuforums.org/showpost.php?p=1666871&postcount=3]("http://ubuntuforums.org/showpost.php?p=1666871&postcount=3")

---

### Post by cdtech on 2008-09-03
I haven't used this myself but should work. Did you clean the repository after the removal:
```
sudo apt-get autoclean && sudo apt-get autoremove
```
This would clean any left over remnants of the removed package.

just a thought.....

---


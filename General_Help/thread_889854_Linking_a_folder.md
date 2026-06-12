---
title: "Linking a folder"
date: 2008-08-14
forum: General Help
---

### Post by 7raTEYdCql on 2008-08-14
Is it possible to line m /var/cache/apt/archives folder with somethng that exists on my home folder. Which will update itself whenever i install new packages.

```
sudo ln -s /var/cache/apt/archives archives
```

Will this command do it. *Note i made a symlink because my root directory is on another partition which my home directory is not.


Will the command make a directory ~/archives and link to it, and will the link be updated everytime i make changes in my /var/cache/apt/archives  folder, or will the changes be made everytime i become root only???

Am slightly confused , neeed help..

---

### Post by 7raTEYdCql on 2008-08-14
or should the code havethis slight modification.
```
sudo ln -s /var/cache/apt/archives /home/mehrzad/archives
```

---

### Post by sujoy on 2008-08-14
that will create a symlink to /var/cache/ark/archives to the current working directory.

syslinks are not directories, just a link. so when you open archives from the current directory like say cd archives, you will actually be taken to /var/cache/atp/archives

hence any change made to that directory will also be visible since you will be accessing that directory itself

---

### Post by sujoy on 2008-08-14
> **i.mehrzad said:**
> or should the code havethis slight modification.
```
sudo ln -s /var/cache/apt/archives /home/mehrzad/archives
```

yes if you want to place the symlink in your home directory and your current working directory is not the home directory

if you enter the previous command from /home/mehrzad then both the commands will do the same thing.

---

### Post by 7raTEYdCql on 2008-08-14
Now if i format my root directory then will the link in my home directory get erased???

I think it does, because it is not a hard link. Now how can i avoid this from happening?/?

---

### Post by sujoy on 2008-08-14
if you format the "/" directory then the link will be invalid and hence a dead link that will be there, but wont work.

one option would be to keep /var in a separate partition.

---

### Post by 7raTEYdCql on 2008-08-14
But if var is in a seperate partition then if i change the distribution then will there be any change. Like suppose if i later change to suse which uses suse then their structure of var will be different. Then there will be no use of that.

Is the only solution AptonCD.

---

### Post by sujoy on 2008-08-15
aptoncd is good if you just want to keep a backup of the package archive. you could just change the symlink manually every time you change the distribution.

---


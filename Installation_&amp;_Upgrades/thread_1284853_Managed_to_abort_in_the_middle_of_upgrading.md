---
title: "Managed to abort in the middle of upgrading"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by catolh on 2009-10-07
Hello

As the title says, i managed to abort in the middle of my upgrade to karmic koala. I was asked if i wanted to remove outdated packages, and i selected "d" for details. And when i wanted to exit from the list i stupidly pressed ctrl+c, and exited from everything.

Now i do not know what to do, to continue the upgrade!

Is there some magical way to resume from where i exited? Or is there some way i can rerun the upgrade?

I feel so stupid right now :\

---

### Post by Cheezespread on 2009-10-07
Check in the update-manager if the option: " a new release is available " is present . You could resume it most probably.

```
sudo update-manager -d
```

---

### Post by catolh on 2009-10-07
> **Cheezespread said:**
> Check in the update-manager if the option: " a new release is available " is present . You could resume it most probably.

```
sudo update-manager -d
```
I am doing this through ssh, i am not anywhere near my box at the moment. 

So i had to do sudo do-release-upgrade -d, but i get the output:
```

$ sudo do-release-upgrade -d
Checking for a new ubuntu release
No new release found

```

---


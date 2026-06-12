---
title: "No Experimental Drivers"
date: 2011-05-31
forum: Hardware
---

### Post by faillord adam on 2011-05-31
After I deleted the propriety graphics drivers, there are no experimental drivers in Jockey. Is there a way to install them from the command line?

---

### Post by Yellow Pasque on 2011-05-31
What proprietary drivers? For ATI, just:
```
sudo apt-get install fglrx
```
or see this for manually installing latest Catalyst from ATI: [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually)

For nvidia:
```
sudo apt-get install nvidia-current
```

---

### Post by coffeecat on 2011-05-31
If you mean the experimental package to get 3d acceleration with the nouveau driver for nvidia cards, the package you need is libgl1-mesa-dri-experimental. Either use Synaptic, or from the command line:

```
sudo apt-get install libgl1-mesa-dri-experimental
```So long as the proprietary nvidia driver is properly uninstalled, simply log out and in again.

---

### Post by faillord adam on 2011-05-31
> **Temüjin said:**
> What proprietary drivers? For ATI, just:
```
sudo apt-get install fglrx
```
or see this for manually installing latest Catalyst from ATI: [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually)

For nvidia:
```
sudo apt-get install nvidia-current
```
Those are the proprietary drivers I was talking about.

---

### Post by faillord adam on 2011-05-31
> **coffeecat said:**
> If you mean the experimental package to get 3d acceleration with the nouveau driver for nvidia cards, the package you need is libgl1-mesa-dri-experimental. Either use Synaptic, or from the command line:

```
sudo apt-get install libgl1-mesa-dri-experimental
```So long as the proprietary nvidia driver is properly uninstalled, simply log out and in again.
I don't know if that's it. I tried it anyway, but my resolution is still messed up. I meant the experimental drivers that can be installed from Jockey.

---

### Post by coffeecat on 2011-05-31
What video card do you have?

---

### Post by faillord adam on 2011-05-31
> **coffeecat said:**
> What video card do you have?
GeForce Go 7300.

---

### Post by coffeecat on 2011-05-31
The libgl1-mesa-dri-experimental package I mentioned earlier is the experimental "driver" that Jockey offers for nvidia cards. And it does disappear as a choice from Jockey when you use the nvidia proprietary driver - I've seen this myself but I don't know why. Anyway, installing that package from the command line or Synaptic is the same as enabling it from Jockey.

Having said all that, I seem to remember reading that there is a problem with some or all of the Geforce 7*** series In Natty. You might want to search the forum for this, or perhaps someone else may have more details.

---


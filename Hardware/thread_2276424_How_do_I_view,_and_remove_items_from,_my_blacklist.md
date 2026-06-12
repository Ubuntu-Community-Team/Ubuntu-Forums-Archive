---
title: "How do I view, and remove items from, my blacklist"
date: 2015-05-02
forum: Hardware
---

### Post by danielandrews7396 on 2015-05-02
Hi Guys,

I've recently become the proud owner of a new Dell XPS 13 Dev Ed, and was having a few issues with my trackpad, so I followed a few threads here on the forums
which suggested that blacklisting my trackpad because it was running PS/2 and not I2C. Anyway, after rebooting, the trackpad doesn't work at all!

I entered the following into my terminal:

echo -e "\n# remove psmouse because we want the mouse to work over I2C bus\nblacklist psmouse" | sudo tee -a /etc/modprobe.d/blacklist.conf

sudo update-initramfs -u

does anyone know how I can reverse this?

Any help would be greatly appreciated!

Thanks,

Dan

---

### Post by dino99 on 2015-05-02
> **danielandrews7396 said:**
> Hi Guys,

I've recently become the proud owner of a new Dell XPS 13 Dev Ed, and was having a few issues with my trackpad, so I followed a few threads here on the forums
which suggested that blacklisting my trackpad because it was running PS/2 and not I2C. Anyway, after rebooting, the trackpad doesn't work at all!

I entered the following into my terminal:

echo -e "\n# remove psmouse because we want the mouse to work over I2C bus\nblacklist psmouse" | sudo tee -a /etc/modprobe.d/blacklist.conf

sudo update-initramfs -u

does anyone know how I can reverse this?

Any help would be greatly appreciated!

Thanks,

Dan

> sudo nano  /etc/modprobe.d/blacklist.conf
then you should see a '#' before 'psmouse', which is how we do comment; so remove that #
or if psmouse is not seen, then add it, save the file and exit from nano, then update again: > sudo update-initramfs -u

---

### Post by danielandrews7396 on 2015-05-02
Hi there dino99!

You absolute legend! Thank you very much, that's done the trick :p

I don't suppose you've any idea on fixing the jumpy trackpad issue on the xps 13 do you? lol.

Thanks again,

Dan

---


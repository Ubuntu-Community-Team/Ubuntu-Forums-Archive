---
title: "Wifi light on Kubuntu"
date: 2006-08-22
forum: Hardware &amp; Laptops
---

### Post by GoodPanos on 2006-08-22
Does any one know how to make the Wifi light turn on every time I turn on my Wifi in Kubuntu?

I have a Dell Inspiron 6000 with the ipw2200 card.  The Wifi works beautifully right off the back.

---

### Post by ltmon on 2006-08-22
I can turn mine on and off with:
```

echo 1 > /proc/acpi/asus/wled
echo 0 > /proc/acpi/asus/wled

```
but that seems to be all I can do.  Yours may be similar, or not, it depends on the laptop manufacturer whether this works or not.

I haven't found a way to link this to the actual state of the wireless card, or to get it to flash on traffic.

L.

---

### Post by vayde on 2006-09-02
Check this out:
[http://ubuntuforums.org/showthread.php?t=119978](http://ubuntuforums.org/showthread.php?t=119978)

---


---
title: "Giving Scanner Access Permission in Jaunty"
date: 2009-06-17
forum: Hardware
---

### Post by technoshaun on 2009-06-17
I have successfully gotten my scanner to work by issuing the command "sudo xsane" However, being that this is a BAD (VERY BAD) practice I would rather access the scanner as a user, which fails. Where and what do I need to modify to give user access to my scanner?

---

### Post by kuadra on 2009-08-10
Some time ago udev was used to set scanner permissions, which would require a user to be in the "scanner" group, and an udev-rule which would set the group ID of the scanning device to "scanner".

Lately the Ubuntu developers have switched to HAL for handling permission on such devices like scanners, cameras, etc. because it provides better granularity to handle permissions.

I've recently setup my Brother DCP-115C Printer/Scanner with this method and will use it as an example below.

If the scanner connected via USB, issue the following command to get the vendor_id and product_id of your scanner:

```
$ lsusb
...
Bus 002 Device 006: ID 04f9:018c Brother Industries, Ltd DCP-115C
...

```

In my case, the vendor_id is "04f9" and the product_id is "018c".

HAL's device information files (*.fdi) can be stored in **/usr/share/hal/fdi/** (used by packages) and **/etc/hal/fdi/** (for custom changes/additions).
You can find already registered scanners in **/usr/share/hal/fdi/preprobe/10osvendor/20-libsane.fdi** and **/usr/share/hal/fdi/preprobe/10osvendor/20-libsane-extras.fdi**

In my case, I've created a new file called **/etc/hal/fdi/preprobe/dcp-115c.fdi** with the following content:

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.subsystem" string="usb">
      <!-- Brother DCP-115C -->
      <match key="usb.vendor_id" int="0x04f9">
        <match key="usb.product_id" int="0x018c">
          <append key="info.capabilities" type="strlist">scanner</append>
          <merge key="scanner.access_method" type="string">proprietary</merge>
        </match>
      </match>
    </match>
  </device>
</deviceinfo>
```

Remember to change the values of vendor_id and product_id.

Now, after restarting the HAL daemon and pluggin in your scanner, xsane should stop complaining about wrong permissions.

```
$ sudo /etc/init.d/hal restart
```

Hope it helps.

---

### Post by serrs on 2009-10-02
This is the right way to do it!  Thanks!

There are piles of hacks out there (even recently).  I wish there was a way to promote this post in searches.  I spent 30 minutes looking at UDEV rules.  :(

---

### Post by kuadra on 2009-12-18
Strangely enough, this method doesn't seem to work in (K)ubuntu 9.10 any more, at least for myself.
I've posted some of my experience and a possible solution (probably only a workaround) in this [thread]("http://ubuntuforums.org/showpost.php?p=8519999&postcount=2").

---


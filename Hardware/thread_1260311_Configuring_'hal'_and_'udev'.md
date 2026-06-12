---
title: "Configuring 'hal' and 'udev'"
date: 2009-09-07
forum: Hardware
---

### Post by Silvernail on 2009-09-07
This is a response from a message I posted in the 'alt.OS.Linux' newgroup.
[http://groups.google.ca/group/alt.os.linux/msg/a605a13588ef6fa7?](http://groups.google.ca/group/alt.os.linux/msg/a605a13588ef6fa7?)

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- xml -*- -->

<deviceinfo version="0.2">
  <device>

    <match key="storage.bus" string="usb">
      <match key="@storage.originating_device:usb.vendor_id" int="0x090c">
        <match key="@storage.originating_device:usb.product_id" int="0x1000">
          <merge key="storage.drive_type" type="string">memory_stick</merge>
        </match>
      </match>
    </match>

  </device>
</deviceinfo> 

I need to connect 3 devices, a USB s-video capture card, a Memorex MP3 player, and a 1TB USB external hard drive.

If I create a file 'my.fdi' in /etc/hal/fdi/policy/, what do I use in place of 'memory_stick'? The product and vendor ID I can get using 'lsusb'.

My OS is Ubuntu 8.04 with all updates. And a fresh install.

---


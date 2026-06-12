---
title: "iPhone and Banshee"
date: 2011-08-01
forum: Hardware
---

### Post by SteinbergerNate on 2011-08-01
Hello,

When I was using 10.04, I didn't have any trouble with my iPhone 3gs syncing with Banshee. I recently upgraded (backed up my data and started with a fresh /home/ as well) to 11.04 and the computer sees the iPhone as does Banshee. However, when I go to sync, I get an error saying that the MP3 format is not compatible with this device for every file that tries to sync.

Now, I know that the iPhone doesn't support much, but it does support MP3. I thought the issue had something to do with HAL until I discovered that HAL had been replaced by udisks or something. It seems that there is some setting or config that is telling the OS or Banshee that this device can't read MP3s so don't even try. Anyone know what that could be? I think it may be  /usr/share/hal/fdi/information/20thirdparty/31-apple-mobile-device.fdi but I'm not sure. And if it is, I don't know what needs to be changed. I'll go ahead and post the contents of that file.

```
<?xml version="1.0"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.subsystem" string="usb">
      <match key="usb.vendor_id" int="0x05ac">
        <match key="usb.product_id" compare_ge="0x1290">
          <match key="usb.product_id" compare_le="0x12af"> 
            <match key="usb.interface.number" int="0x1">
              <append key="info.capabilities" type="strlist">afc</append>
            </match>
          </match>
        </match>
      </match>
    </match>
  </device>
</deviceinfo>
```

---


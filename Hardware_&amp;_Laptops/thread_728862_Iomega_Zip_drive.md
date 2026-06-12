---
title: "Iomega Zip drive"
date: 2008-03-19
forum: Hardware &amp; Laptops
---

### Post by Ryukage on 2008-03-19
I recently pulled an IDE ZIP drive out of an old Compaq system that I'm retiring and put it into my Linux machine, at the same time that I installed Kubuntu 7.10. Kubuntu detected the hardware and created device nodes for it, but that was it.  I manually created a mount point and added it to fstab, giving me partial support, but it still doesn't work the way I'd like.

While the HAL is aware of the drive, and will (un)mount with explicit DCOP calls, it won't poll it for media insertion events, nor will it dynamically create a desktop icon for it like it does for optical and USB media, even when I mount it manually.  The drive also does not appear in the media: kioslave, even when mounted manually.  Windows is able to detect ZIP disk insertion events and respond appropriately, so I don't see why Linux shouldn't as well.

I can understand the HAL refusing to poll a floppy drive; they can't tell whether they've got a disk in them or not, so polling would cause problems.  But ZIP drives, like optical drives, "know" whether there's a disk inserted or not, so they should be pollable.

I can, of course, make a "link to device" icon manually, but that is less than satisfactory: the icon so created is there all the time even when there's no disk in the drive, and doesn't track the mounted/unmounted state correctly under some conditions. (Specifically, if I just open the icon and let it automount, rather than right-clicking and mounting explicitly, or if I mount it from a CLI, the icon goes a little haywire: it shows as unmounted normally, but changes to mounted when hovered.) Also, I prefer the kicker media applet over the desktop icons, but the zip drive doesn't show there because the media: kioslave doesn't recognize it.

So, is there any way I can get my ZIP drive to behave like other removable media, with media insert notifications, automatic desktop icon, and a media:/ icon?

As an aside, the filesystems module in System Settings seems to be confused by the line I added to the fstab for the ZIP drive.  It displays the mountpoint for the ZIP drive in the line for the optical drive, and displays no information in the line for the ZIP drive.  Doesn't seem to be a problem, as the device listings from the HAL show everything correctly, but indicates a bug of some sort in that software.

---


---
title: "external hardrive mount problem (hal configuration?)"
date: 2008-05-25
forum: Hardware
---

### Post by erwanj on 2008-05-25
Hey,


I have permission and owner problems with an external hardrive.
The hardrive mounts automatically I can access it from the Desktop or in /media/disk but it is mounted with 755 permissions, root owner and root group.
I suppose that I have to custom hal behavior. So I should modify /etc/hal/fdi/policy/preferences.fdi and add something like this :
```
  <device>
    <match key="block.is_volume" bool="true">
          <merge key="volume.policy.mount_option.uid" type="int">1000</merge>
    </match>
  </device>

```
I am not sure of the keys I can use. I have checked searching for the volume.mount.valid_options of my device with hal-device. But I don't where I can find the types of theses options. I supposed the volume.policy.mount_option.uid key is an integer.

Would someone have any clue?

I have seen others fdi files in /usr/lib/hal/, I am supposed to modify the /etc/hal/ or the /usr/lib/hal/ ones?

Thanks.

---


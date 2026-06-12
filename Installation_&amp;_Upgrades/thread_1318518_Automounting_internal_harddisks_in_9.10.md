---
title: "Automounting internal harddisks in 9.10"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by Bao2 on 2009-11-07
When you want access a internal hard disk PolicyKit is there always to annoy you asking for password. To avoid that you can edit this file:

gksudo gedit /usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy

And search for this entry:

```
  <action id="org.freedesktop.devicekit.disks.filesystem-mount-system-internal">
    <description>Mount a system-internal device</description>
    <description xml:lang="da">Montér en intern enhed</description>
    <description xml:lang="de">Eingebautes Gerät einhängen</description>
    <message>Authentication is required to mount the device</message>
    <message xml:lang="da">Autorisering er påkrævet for at montere et fil system</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um das Gerät einzuhängen</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>
```

and change the "allow_active" line to this:

<allow_active>yes</allow_active>

And now you can access all your harddisk without being annoyed again for passwords.:D

---


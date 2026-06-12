---
title: "sudo netplan apply does not update the LAN IP as expected"
date: 2020-10-17
forum: Hardware
---

### Post by thosecars822 on 2020-10-17
Hello

I wondered why sudo netplan apply did not updte the LAN IP as expected.

I have 01-netcfg.yaml and 01-network-manager-all.yaml under /etc/netplan in Ubuntu.

The content of /etc/netplan/01-netcfg.yaml is:
```

# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
  version: 2
  renderer: networkd
  ethernets:
    enp2s0:
      dhcp4: no
      addresses:
        - 192.168.1.80/24
      gateway4: 192.168.1.1
      nameservers:
          addresses: [8.8.8.8, 1.1.1.1]

```

and

The content of /etc/netplan/01-network-manager-all.yaml is:
```

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager

```

Then I realized that when I do "sudo netplan apply", the LAN IP address only gets updated in case I remove the file /etc/netplan/01-network-manager-all.yaml in advance.

I do not want to remove /etc/netplan/01-network-manager-all.yaml because it was in that location after Ubuntu installation and I do not want to break anything.

What should I do so that "sudo netplan apply" worked to change the LAN IP even if the file /etc/netplan/01-network-manager-all.yaml exists?

Thanks in advance

---

### Post by Tadaen_Sylvermane on 2020-10-17
Just change it's name if you want it stopped. Netplan won't run anything other than a .yaml file near as I can tell. I just change the default files to end with .bak or .orig or something. Effectively disables them while not eliminating them.

```
sudo mv [COLOR=#000000]/etc/netplan/01-network-manager-all.yaml [/COLOR]/etc/netplan/01-network-manager-all.yaml.orig
```

That or you can comment out all lines inside of the file, with the same invisible result.

*EDIT* A note. It won't break anything really. When I do debootstrap installations it doesn't even create a netplan yaml file. I have to create it myself. Doesn't seem to matter what I name it aside from the first 2 characters being a number between 01 - 99. The machine will still boot like normal, just without network of any kind.

---


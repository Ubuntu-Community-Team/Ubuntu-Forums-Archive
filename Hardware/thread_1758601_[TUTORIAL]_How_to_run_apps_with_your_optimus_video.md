---
title: "[TUTORIAL] How to run apps with your optimus video card"
date: 2011-05-14
forum: Hardware
---

### Post by cdesseno on 2011-05-14
Now it is possible to use your Nvidia Optimus video card through VirtualGL. This tutorial shows how. Bumblebee was made by MrMEEE, all credits go to him.
Project repo: [URL="https://github.com/MrMEEE/bumblebee"]https://github.com/MrMEEE/bumblebee
[/URL]
You may submit any bug in github's issues.

[SIZE="3"][COLOR="Red"]**This project is very active and currently is being developed!! So do it at your own risk!**[/COLOR][/SIZE]

1) First clone the last version of bumblebee:
```
git clone https://github.com/MrMEEE/bumblebee.git
```

2) Cd  the directory:
```
cd bumblebee
```

3) Make the file executable:
```
sudo chmod +x install.sh
```

4) Run the installer:
```
sudo ./install.sh
```

5) Follow the installation steps.

6) Reboot.

7) To run apps:
```
optirun32 [appname]
```
or
```
optirun64 [appname]
```

To uninstall run install-files/bumblebee-uninstall.

Note: just to test the huge difference you can run glxgears and show your results here.

---


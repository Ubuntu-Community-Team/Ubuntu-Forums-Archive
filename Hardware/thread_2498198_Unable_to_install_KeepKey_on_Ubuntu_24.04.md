---
title: "Unable to install KeepKey on Ubuntu 24.04"
date: 2024-06-03
forum: Hardware
---

### Post by aleoje on 2024-06-03
I am unable to install KeepKey on the latest version of Ubuntu. Something about externally managed packages error. Can anyone provide instructions? Thank you!

---

### Post by wavesonfine on 2024-06-16
> **aleoje said:**
> I am unable to install KeepKey on the latest version of Ubuntu. Something about externally managed packages error. Can anyone provide instructions? Thank you! [SIZE=1][[COLOR=white]dordle[/COLOR]]("https://dordle.io")[/SIZE]
It seems there might be a confusion with the Ubuntu version number you mentioned (Ubuntu 24.04). As of my last update, the latest Ubuntu LTS version is 20.04 (Focal Fossa). If you meant Ubuntu 20.04, here’s how you can install KeepKey:


1. Add the KeepKey Repository: Open a terminal and add the KeepKey repository to your system:
   ```bash
    sudo add-apt-repository ppa:keepkey/keepkey
   ```


2. Update Package List: Update your package list to include the new repository:
   ```bash
   sudo apt-get update
   ```


3. Install KeepKey Client: Finally, install the KeepKey client software:
   ```bash
   sudo apt-get install keepkey
   ```


4. Launch KeepKey: After installation, you should be able to launch the KeepKey client from your applications menu or by typing `keepkey` in the terminal.


If you encounter any specific errors or issues during these steps, please provide more details so I can assist you further.

---


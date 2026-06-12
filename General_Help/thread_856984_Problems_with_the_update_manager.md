---
title: "Problems with the update manager"
date: 2008-07-12
forum: General Help
---

### Post by survient on 2008-07-12
anybody getting results similar to this recently in the update manager?:
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler2_0.6.4-1ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler2_0.6.4-1ubuntu2_amd64.deb)
  404 Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler-glib2_0.6.4-1ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler-glib2_0.6.4-1ubuntu2_amd64.deb)
  404 Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/linux-restricted-modules-common_2.6.24.13-19.44_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/linux-restricted-modules-common_2.6.24.13-19.44_all.deb)
  404 Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-restricted-modules-2.6.24/linux-restricted-modules-2.6.24-19-rt_2.6.24.13-19.44_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-restricted-modules-2.6.24/linux-restricted-modules-2.6.24-19-rt_2.6.24.13-19.44_amd64.deb)
  404 Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-19.44_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-19.44_amd64.deb)
  404 Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/poppler-utils_0.6.4-1ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/poppler-utils_0.6.4-1ubuntu2_amd64.deb)
  404 Not Found [IP: 91.189.88.31 80]

---

### Post by iaculallad on 2008-07-12
Does it display the same error when you issue the command below on your terminal?

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by survient on 2008-07-12
for some reason it was able to update when using the terminal, and then it had a few more updates in the update manager that went through fine. All I need now is a way to get another update notifier that checks my server when it has updates.......... been wanting that for some time now....

---


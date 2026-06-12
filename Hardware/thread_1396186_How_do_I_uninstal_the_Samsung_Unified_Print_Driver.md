---
title: "How do I uninstal the Samsung Unified Print Drivers that were installed by .tar?"
date: 2010-02-01
forum: Hardware
---

### Post by Carlo1973 on 2010-02-01
Hi there,

I'm 99% done getting my Ubuntu box up and running. I tried to install the drivers for my printer today - Samsung CLP-310N. 

I think I goofed when I installed them. Should have done some research. The version 1 drivers on their website are in tar compressed format. After installing them and AFTER doing some research I found that there were issues and that there were already pre-compiled .deb packages that are newer than what is shown on Samsung's website and work properly. However now I have to uninstall the old ones before I can install the new ones.

How do I uninstall these old drivers now?

Thanks

Carlo

---

### Post by samantha_ on 2010-02-01
> **Carlo1973 said:**
> Hi there,

I'm 99% done getting my Ubuntu box up and running. I tried to install the drivers for my printer today - Samsung CLP-310N. 

I think I goofed when I installed them. Should have done some research. The version 1 drivers on their website are in tar compressed format. After installing them and AFTER doing some research I found that there were issues and that there were already pre-compiled .deb packages that are newer than what is shown on Samsung's website and work properly. However now I have to uninstall the old ones before I can install the new ones.

How do I uninstall these old drivers now?

Thanks

Carlo

Go to the folder where you compiled them, and run
```

sudo make uninstall
```

---

### Post by Carlo1973 on 2010-02-01
I was about to say that it wasn't compiled from source but was installed with a pre-compiled script called "install.sh" but then I had a brain wave and checked a bit deeper in the folder structure - there was an uninstall.sh script file. DUH! I can't believe I had such a brain shutdown!

Thanks Samantha for that smack upside the head! :)

---


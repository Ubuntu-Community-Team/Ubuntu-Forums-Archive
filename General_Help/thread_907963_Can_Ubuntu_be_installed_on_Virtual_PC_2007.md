---
title: "Can Ubuntu be installed on Virtual PC 2007?"
date: 2008-09-02
forum: General Help
---

### Post by kamala27 on 2008-09-02
Hello Guys, I'm a newbie here and will like to know if Ubuntu can be installed on Microsoft Virtual PC 2007?
Bcos, I'm having probs installing it on V PC.
Thanks in advance for your assistance.

---

### Post by b20963a2 on 2008-09-02
It does work in Hyper-V. (Not really an answer to your question though...)

---

### Post by kamala27 on 2008-09-02
Thank you for your response, will download the Hyper-V now and get back to you later. One more thing, is it a standalone program? On Microsft site it seems it is embedded in Windows Sever 2008.

---

### Post by b20963a2 on 2008-09-02
Indeed, it is a feature of Windows Server 2008. You first need to install W2K8 and then select Hyper-V as an additional component.

/edit: the only catch is that you need to remove the "synthetic NIC" and replace it with a "legacy NIC" in the settings of your virtual machine

---


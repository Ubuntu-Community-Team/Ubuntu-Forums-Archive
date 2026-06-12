---
title: "[SOLVED] No earth in GoogleEarth"
date: 2008-11-02
forum: General Help
---

### Post by scweston on 2008-11-02
Hi,

I'm hoping someone will be able to help me solve my problem with googleearth. The problem is that when I start up google earth everything appears to go as normal, but no earth appears. I just get space with the stars in it.

However, if I do start it with root privileges it works perfectly.

I installed googleearth  on intrepid amd64 version.

When run without root privileges from the terminal I get no error messages appearing.

Any help will be much appreciated.

Stephen

Edit: just thought I should add that I installed using the binary downloaded from the google site.

---

### Post by _sAm_ on 2008-11-02
In Google Earth go to: 
View > Switch to Earth

or..?

---

### Post by scweston on 2008-11-02
Hi,

Thank you for your suggestion _sAm_. Unfortunately it wasn't that simple. It was already set to view Earth.

I have however, despite searching for ages on these ubuntu forums to find a solution, I did a general google search and found my answer.

The solution which I found and worked for me was to delete the folder ~/.config/Google and it's contents. I used these commands: -

sudo rm ~/.config/Google/GoogleEarthPlus.conf
sudo rmdir ~/.config/Google

I believe this is a permissions issue, as the directory was owned by root. After deleteing them and restarting googleearth they folder was recreated with different ownership.

Stephen

---

### Post by 4ebees on 2008-11-17
A simple solution to an irritating problem.

Let me say Well Done and Thank You Very Much.



> **scweston said:**
> Hi,

Thank you for your suggestion _sAm_. Unfortunately it wasn't that simple. It was already set to view Earth.

I have however, despite searching for ages on these ubuntu forums to find a solution, I did a general google search and found my answer.

The solution which I found and worked for me was to delete the folder ~/.config/Google and it's contents. I used these commands: -

sudo rm ~/.config/Google/GoogleEarthPlus.conf
sudo rmdir ~/.config/Google

I believe this is a permissions issue, as the directory was owned by root. After deleteing them and restarting googleearth they folder was recreated with different ownership.

Stephen

---


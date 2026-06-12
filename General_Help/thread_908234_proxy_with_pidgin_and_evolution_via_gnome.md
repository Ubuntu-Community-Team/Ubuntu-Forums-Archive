---
title: "proxy with pidgin and evolution via gnome"
date: 2008-09-02
forum: General Help
---

### Post by nkobel003 on 2008-09-02
My school requires a proxy with no password protection in order to use the internet. I set firefox to use the proxy, and I also changed the GNOME settings to use the proxy with no password; however, pidgin and evolution do not connect, while firefox does.

Can anyone help correct this error?

---

### Post by aloshbennett on 2008-09-02
Under Advanced Settings of your connection details, you could specify the proxy settings. You could either give your proxy there or select an option to use gnome proxy.

---

### Post by nkobel003 on 2008-09-04
Firefox works fine no matter whether I tell it to use GNOME settings or enter it in manually, but pidgin and evolution do not work (i.e. pidgin will not sign in and evolution will not collect mail.)

Thus, my proxy settings in GNOME are correct, so it must be something with pidgin or evolution. The command sudo apt-get update/upgrade also work, so it is definitely not GNOME's fault.

Does anyone know how to correct the settings in Pidgin and Evolution? I told pidgin to use the GNOME settings, but it still doesn't work!

Nick

---

### Post by aloshbennett on 2008-09-04
Have you tried setting the proxy directly in pidgin?

---

### Post by nkobel003 on 2008-09-04
Ok, I deleted and added my accounts on Pidgin and now it works, but I don't know for evolution. I will try deleting and adding again to see if it works, but I have other plans right now, so I'll do it later.

---

### Post by nkobel003 on 2008-09-07
Evolution still doesn't work with a proxy. Does anyone know how to get it to work? I switch back and forth from using the school's proxy to my host family's direct connection, so it would seem to be simple...

---


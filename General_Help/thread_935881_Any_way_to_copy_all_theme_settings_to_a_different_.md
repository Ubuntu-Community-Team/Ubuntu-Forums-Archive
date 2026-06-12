---
title: "Any way to copy all theme settings to a different user?"
date: 2008-10-02
forum: General Help
---

### Post by Gizim on 2008-10-02
I have my main account setup the way i like with a different theme and all the personalized jazz but is there a way to move that to another account as well? Like my girl friend account so its not so "normal"? Thanks!

---

### Post by Ms_Angel_D on 2008-10-02
Emerald, Metacity, and Icons are located in your home folder. User ctrl+h to view hidden folders so you can copy them.

Emerald themes
```
/home/USERNAME/.emerald
```

Other Themes
```
/home/USERNAME/.themes
```

Icon Themes
```
/home/USERNAME/.icons
```

Once you have copied them to the same location in her home folder make sure you give her ownership

```
sudo chown -R USERNAME /home/USERNAME/.FOLDER_NAME/
```

The -R flag does this recursively so that all files under that folder will be owned by the new owner.

---

### Post by MunkyJunky on 2008-10-02
Another method would be right click your desktop, go to 'Change Background', then open up the 'Themes' tab. If your using a custom theme, then 'custom' will be selected as your theme. Click on it, then 'Save Theme' at the bottom. Port that theme file however you want to your new desktop, and install it as a theme.

---


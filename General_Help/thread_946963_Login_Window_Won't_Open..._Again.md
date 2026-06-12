---
title: "Login Window Won't Open... Again"
date: 2008-10-13
forum: General Help
---

### Post by Unanimated on 2008-10-13
...This happened a while ago. Same exact problem - login window would open for about a second, close, and not let me back in. Last time, I solved it by reinstalling my video drivers and doing sudo dpkg-reconfigure gdm. I've reinstalled my video drivers about 13,000 (sarcasm) times due to heavy modifying of xorg.conf, and dpkg-reconfigure returns this:
```
sam@sam-desktop:~$ sudo dpkg-reconfigure gdm
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
                                                                         [ OK ]
In file "/usr/share/menu/autopackage-gtk", at (or in the definition that ends at) line 1:
[...]&#1085;&#1080;&#1084; &#1055;&#1054;\\nName[sq]=Administro \"software" palësh të treta\\nName[sv]=Hantera tredjepartsprogramvara\\nStartupNotify=true\\nTerminal=false\\nType=Application\\n"
[...]                                                 ^
Expected: "="
Skipping file because of errors...

```

This is what my autopackage-gtk looks like:
```
?package(local.autopackage-gtk):needs="x11" section="System Tools" command="autopackage-manager-gtk" icon="kpackage48" title="Manage 3rd party software" kde_opt="X-Autopackage=@autopackage.org/autopackage-gtk:1.2.5\\nEncoding=UTF-8\\nName[ar]=&#1573;&#1583;&#1575;&#1585;&#1577; &#1576;&#1585;&#1575;&#1605;&#1580; &#1575;&#1604;&#1591;&#1585;&#1601; &#1575;&#1604;&#1579;&#1575;&#1604;&#1579;\\nName[cs]=Spravovat software t&#345;etích stran\\nName[de]=Verwaltung der Software von Drittanbietern\\nName[es_CO]=Administrador de software de terceros\\nName[fr]=Gérer le programme d'une 3éme partie\\nName[hu]=Egyéb szoftverek kezelése\\nName[it]=Gestisci programmi di terze parti\\nName[nl]=Extra software beheren\\nName[pa]=3&#2588;&#2631; &#2599;&#2623;&#2608; &#2616;&#2622;&#2603;&#2591;&#2613;&#2631;&#2565;&#2608; &#2602;&#2608;&#2604;&#2672;&#2599;\\nName[ru]=&#1059;&#1087;&#1088;&#1072;&#1074;&#1083;&#1077;&#1085;&#1080;&#1077; &#1089;&#1090;&#1086;&#1088;&#1086;&#1085;&#1085;&#1080;&#1084; &#1055;&#1054;\\nName[sq]=Administro \"software" palësh të treta\\nName[sv]=Hantera tredjepartsprogramvara\\nStartupNotify=true\\nTerminal=false\\nType=Application\\n"
```

Yeah... I'm sure I could just skip this due to Intrepid's release in a few days, but I want to solve it just in case it happens in Intrepid.

---

### Post by Unanimated on 2008-10-26
bump

---


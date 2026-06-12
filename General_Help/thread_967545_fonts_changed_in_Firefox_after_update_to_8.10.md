---
title: "fonts changed in Firefox after update to 8.10"
date: 2008-11-02
forum: General Help
---

### Post by snitko on 2008-11-02
After I upgraded to 8.10, Firefox started to render some pages with the wrong font. I had "DejaVu" family set for all types of fonts in FireFox settings and in "Gnome Appearance", but some pages now use a different font.

I guess it's just that new Ubuntu has some new fonts included, that are used instead of DejaVu, because these fonts are listed in page's css. So, I tried substituting it in ~/.fonts/fonts.conf with the following:

```
 <selectfont>
   <rejectfont>
     <pattern><patelt name="family"><string>Tahoma</string></patelt></pattern>
   </rejectfont>
 </selectfont>

 <alias>
   <family>Tahoma</family>
   <prefer>
      <family>DejaVu</family>
   </prefer>
 </alias>
```

Didn't work with Arial and Sans either. Any ideas?

---


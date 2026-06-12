---
title: "No Visual efects in Maveric"
date: 2010-09-30
forum: Hardware
---

### Post by tadaskr on 2010-09-30
Hello everyone, 
Last night I installed kubuntu 10.10 beta and there I can't enebale visual effects. I installed ATI drivers from Additional Drivers but this problem wasn't solved. Maybe someone know how fix this problem? or in Beta release there isn't visual effects? When I going to desktop effects I see "  Desktop effects are not available on this system due to the following technical issues:" but there isn't any listed
Thanks for help

---

### Post by tadaskr on 2010-10-01
bump

---

### Post by Ayuthia on 2010-10-01
You might try going into ~/.kde/share/config and look for:

```

[Compositing]
CheckIsSafe=true

```

If yours show 'false', change it to true and then try it again.  I cannot remember if you need to restart or not though.

---

### Post by tadaskr on 2010-10-02
```

[Compositing]
AnimationSpeed=3
Backend=OpenGL
DisableChecks=false
Enabled=false
GLDirect=true
GLMode=TFP
GLTextureFilter=1
GLVSync=true
HiddenPreviews=5
OpenGLIsUnsafe=true
XRenderSmoothScale=false

```I see this on file kwinrc file on that directory. So i should add that line or change something else?

---

### Post by Ayuthia on 2010-10-06
> **tadaskr said:**
> ```

[Compositing]
AnimationSpeed=3
Backend=OpenGL
DisableChecks=false
Enabled=false
GLDirect=true
GLMode=TFP
GLTextureFilter=1
GLVSync=true
HiddenPreviews=5
OpenGLIsUnsafe=true
XRenderSmoothScale=false

```I see this on file kwinrc file on that directory. So i should add that line or change something else?

You might try adding the line but you might try changing OpenGLIsUnsafe to false also.

---

### Post by hsantanna on 2010-10-08
~/.kde/share/config/kwinrc

[Compositing]
# ...
OpenGLIsUnsafe=false

will turn back the kde composite effects. don't need to change any other line.

---


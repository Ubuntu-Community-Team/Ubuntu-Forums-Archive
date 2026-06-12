---
title: "Problems With installing NS-2(nsnam) a network simulator"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by prabhakaran1989 on 2009-04-24
[B]I tried to install a network simulator for my project .. NS-2 is quite famous...so i downloaded the pakages from sourceforge.net ..ns-allinone pakage..
But i cant install .it shows me the following errors!
what can i do?
any solutions? (alternate simulators ? NAME IT PLEASE!!) i am installing for the 4 th time...d this time it was in UBUNTU 9.04[/B]

Help me!!

> /home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:245: error: ‘TkBorder’ has no member named ‘lightGC’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:246: error: ‘TkBorder’ has no member named ‘hashPtr’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:247: error: ‘TkBorder’ has no member named ‘nextPtr’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:256: error: ‘gcValues’ undeclared (first use in this function)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:256: error: ‘TkBorder’ has no member named ‘bgColorPtr’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:257: error: ‘TkBorder’ has no member named ‘bgGC’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:257: warning: implicit declaration of function ‘Tk_GetGC’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:257: error: ‘GCForeground’ undeclared (first use in this function)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c: In function ‘Tk_Draw3DRectangle’:
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:284: error: expected declaration specifiers before ‘Drawable’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:292: error: argument ‘drawable’ doesn’t match prototype
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tkDecls.h:247: error: prototype declaration
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:292: error: argument ‘border’ doesn’t match prototype
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tkDecls.h:247: error: prototype declaration
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:292: error: number of arguments doesn’t match prototype
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tkDecls.h:247: error: prototype declaration
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:300: warning: passing argument 2 of ‘Tk_3DVerticalBevel’ makes pointer from integer without a cast
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:300: warning: passing argument 3 of ‘Tk_3DVerticalBevel’ makes integer from pointer without a cast
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:300: error: too many arguments to function ‘Tk_3DVerticalBevel’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:302: warning: passing argument 2 of ‘Tk_3DVerticalBevel’ makes pointer from integer without a cast
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:302: warning: passing argument 3 of ‘Tk_3DVerticalBevel’ makes integer from pointer without a cast
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:302: error: too many arguments to function ‘Tk_3DVerticalBevel’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:304: warning: passing argument 2 of ‘Tk_3DHorizontalBevel’ makes pointer from integer without a cast
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:304: warning: passing argument 3 of ‘Tk_3DHorizontalBevel’ makes integer from pointer without a cast
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:304: error: too many arguments to function ‘Tk_3DHorizontalBevel’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:306: warning: passing argument 2 of ‘Tk_3DHorizontalBevel’ makes pointer from integer without a cast
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:306: warning: passing argument 3 of ‘Tk_3DHorizontalBevel’ makes integer from pointer without a cast
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:306: error: too many arguments to function ‘Tk_3DHorizontalBevel’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c: In function ‘Tk_NameOf3DBorder’:
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:333: error: ‘TkBorder’ has no member named ‘hashPtr’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c: At top level:
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:352: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:355: error: expected identifier or ‘(’ before ‘{’ token
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:376: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Tk_3DBorderGC’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:382: error: expected identifier or ‘(’ before ‘{’ token
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c: In function ‘Tk_Free3DBorder’:
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:429: error: ‘Display’ undeclared (first use in this function)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:429: error: ‘display’ undeclared (first use in this function)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:429: warning: implicit declaration of function ‘DisplayOfScreen’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:429: error: ‘TkBorder’ has no member named ‘screen’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:432: error: ‘TkBorder’ has no member named ‘resourceRefCount’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:433: error: ‘TkBorder’ has no member named ‘resourceRefCount’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:437: error: ‘TkBorder’ has no member named ‘hashPtr’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:439: error: ‘TkBorder’ has no member named ‘bgColorPtr’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:440: warning: implicit declaration of function ‘Tk_FreeColor’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:440: error: ‘TkBorder’ has no member named ‘bgColorPtr’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:442: error: ‘TkBorder’ has no member named ‘darkColorPtr’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:443: error: ‘TkBorder’ has no member named ‘darkColorPtr’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:445: error: ‘TkBorder’ has no member named ‘lightColorPtr’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:446: error: ‘TkBorder’ has no member named ‘lightColorPtr’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:448: error: ‘TkBorder’ has no member named ‘shadow’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:448: error: ‘None’ undeclared (first use in this function)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:449: warning: implicit declaration of function ‘Tk_FreeBitmap’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:449: error: ‘TkBorder’ has no member named ‘shadow’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:451: error: ‘TkBorder’ has no member named ‘bgGC’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:452: warning: implicit declaration of function ‘Tk_FreeGC’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:452: error: ‘TkBorder’ has no member named ‘bgGC’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:454: error: ‘TkBorder’ has no member named ‘darkGC’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:455: error: ‘TkBorder’ has no member named ‘darkGC’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:457: error: ‘TkBorder’ has no member named ‘lightGC’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:458: error: ‘TkBorder’ has no member named ‘lightGC’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:461: error: ‘TkBorder’ has no member named ‘nextPtr’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:462: error: ‘TkBorder’ has no member named ‘hashPtr’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:464: error: ‘TkBorder’ has no member named ‘hashPtr’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:464: error: ‘TkBorder’ has no member named ‘nextPtr’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:467: error: ‘TkBorder’ has no member named ‘nextPtr’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:468: error: ‘TkBorder’ has no member named ‘nextPtr’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:470: error: ‘TkBorder’ has no member named ‘nextPtr’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:470: error: ‘TkBorder’ has no member named ‘nextPtr’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:472: error: ‘TkBorder’ has no member named ‘objRefCount’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c: In function ‘FreeBorderObjProc’:
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:535: error: ‘TkBorder’ has no member named ‘objRefCount’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:536: error: ‘TkBorder’ has no member named ‘objRefCount’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:537: error: ‘TkBorder’ has no member named ‘resourceRefCount’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c: In function ‘DupBorderObjProc’:
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:573: error: ‘TkBorder’ has no member named ‘objRefCount’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c: In function ‘Tk_SetBackgroundFromBorder’:
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:601: error: ‘TkBorder’ has no member named ‘bgColorPtr’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c: In function ‘Tk_Draw3DPolygon’:
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:755: error: expected declaration specifiers before ‘Drawable’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:757: error: expected declaration specifiers before ‘XPoint’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:768: error: argument ‘drawable’ doesn’t match prototype
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tkDecls.h:242: error: prototype declaration
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:768: error: argument ‘border’ doesn’t match prototype
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tkDecls.h:242: error: prototype declaration
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:768: error: number of arguments doesn’t match prototype
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tkDecls.h:242: error: prototype declaration
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:769: error: ‘XPoint’ undeclared (first use in this function)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:769: error: expected ‘;’ before ‘poly’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:770: error: expected ‘;’ before ‘perp’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:771: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:771: error: ‘p1Ptr’ undeclared (first use in this function)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:771: error: ‘p2Ptr’ undeclared (first use in this function)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:771: warning: left-hand operand of comma expression has no effect
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:773: error: ‘GC’ undeclared (first use in this function)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:773: error: expected ‘;’ before ‘gc’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:775: error: ‘Display’ undeclared (first use in this function)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:775: error: ‘display’ undeclared (first use in this function)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:775: error: ‘Tk_FakeWin’ has no member named ‘display’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:777: error: ‘TkBorder’ has no member named ‘lightGC’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:777: error: ‘None’ undeclared (first use in this function)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:791: warning: passing argument 2 of ‘Tk_Draw3DPolygon’ makes pointer from integer without a cast
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:791: warning: passing argument 3 of ‘Tk_Draw3DPolygon’ makes integer from pointer without a cast
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:791: error: too many arguments to function ‘Tk_Draw3DPolygon’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:794: warning: passing argument 2 of ‘Tk_Draw3DPolygon’ makes pointer from integer without a cast
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:794: warning: passing argument 3 of ‘Tk_Draw3DPolygon’ makes integer from pointer without a cast
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:794: error: too many arguments to function ‘Tk_Draw3DPolygon’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:803: error: subscripted value is neither array nor pointer
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:804: error: subscripted value is neither array nor pointer
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:850: error: subscripted value is neither array nor pointer
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:850: warning: left-hand operand of comma expression has no effect
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:851: warning: left-hand operand of comma expression has no effect
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:862: warning: implicit declaration of function ‘ShiftLine’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:862: error: ‘newB1’ undeclared (first use in this function)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:863: error: ‘newB2’ undeclared (first use in this function)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:865: error: ‘poly’ undeclared (first use in this function)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:868: warning: implicit declaration of function ‘Intersect’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:868: error: ‘b1’ undeclared (first use in this function)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:868: error: ‘b2’ undeclared (first use in this function)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:900: error: ‘perp’ undeclared (first use in this function)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:903: error: ‘c’ undeclared (first use in this function)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:904: error: ‘shift1’ undeclared (first use in this function)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:905: error: ‘shift2’ undeclared (first use in this function)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:919: error: ‘gc’ undeclared (first use in this function)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:919: error: ‘TkBorder’ has no member named ‘lightGC’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:921: error: ‘TkBorder’ has no member named ‘darkGC’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:923: warning: implicit declaration of function ‘XFillPolygon’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:923: error: ‘Convex’ undeclared (first use in this function)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:924: error: ‘CoordModeOrigin’ undeclared (first use in this function)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c: In function ‘Tk_Fill3DRectangle’:
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:963: error: expected declaration specifiers before ‘Drawable’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:970: error: argument ‘drawable’ doesn’t match prototype
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tkDecls.h:270: error: prototype declaration
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:970: error: argument ‘border’ doesn’t match prototype
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tkDecls.h:270: error: prototype declaration
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:970: error: number of arguments doesn’t match prototype
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tkDecls.h:270: error: prototype declaration
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:997: warning: implicit declaration of function ‘XFillRectangle’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:997: error: ‘Tk_FakeWin’ has no member named ‘display’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:997: error: ‘TkBorder’ has no member named ‘bgGC’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1004: warning: passing argument 2 of ‘Tk_Draw3DRectangle’ makes pointer from integer without a cast
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1004: warning: passing argument 3 of ‘Tk_Draw3DRectangle’ makes integer from pointer without a cast
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1004: error: too many arguments to function ‘Tk_Draw3DRectangle’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c: In function ‘Tk_Fill3DPolygon’:
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1028: error: expected declaration specifiers before ‘Drawable’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1030: error: expected declaration specifiers before ‘XPoint’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1041: error: argument ‘drawable’ doesn’t match prototype
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tkDecls.h:265: error: prototype declaration
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1041: error: argument ‘border’ doesn’t match prototype
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tkDecls.h:265: error: prototype declaration
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1041: error: number of arguments doesn’t match prototype
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tkDecls.h:265: error: prototype declaration
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1044: error: ‘Tk_FakeWin’ has no member named ‘display’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1044: error: ‘TkBorder’ has no member named ‘bgGC’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1045: error: ‘Complex’ undeclared (first use in this function)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1045: error: ‘CoordModeOrigin’ undeclared (first use in this function)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1048: warning: passing argument 2 of ‘Tk_Draw3DPolygon’ makes pointer from integer without a cast
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1048: warning: passing argument 3 of ‘Tk_Draw3DPolygon’ makes integer from pointer without a cast
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1048: error: too many arguments to function ‘Tk_Draw3DPolygon’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c: In function ‘BorderInit’:
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1072: error: ‘TkDisplay’ has no member named ‘borderInit’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1073: error: ‘TkDisplay’ has no member named ‘borderTable’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c: At top level:
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1095: warning: conflicting types for ‘ShiftLine’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1095: error: static declaration of ‘ShiftLine’ follows non-static declaration
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:862: error: previous implicit declaration of ‘ShiftLine’ was here
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c: In function ‘ShiftLine’:
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1096: error: expected declaration specifiers before ‘XPoint’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1097: error: expected declaration specifiers before ‘XPoint’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1102: error: expected declaration specifiers before ‘XPoint’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1138: error: invalid type argument of ‘unary *’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1138: error: invalid type argument of ‘unary *’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1139: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1139: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1140: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1140: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1158: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1164: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c: At top level:
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1188: error: static declaration of ‘Intersect’ follows non-static declaration
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:868: error: previous implicit declaration of ‘Intersect’ was here
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c: In function ‘Intersect’:
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1189: error: expected declaration specifiers before ‘XPoint’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1190: error: expected declaration specifiers before ‘XPoint’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1191: error: expected declaration specifiers before ‘XPoint’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1192: error: expected declaration specifiers before ‘XPoint’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1193: error: expected declaration specifiers before ‘XPoint’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1203: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1203: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1203: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1203: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1204: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1204: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1204: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1204: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1205: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1205: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1205: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1205: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1206: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1206: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1206: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1206: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1211: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1211: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1211: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1211: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1218: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1220: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1222: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1222: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1222: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1222: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1229: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1231: error: invalid type argument of ‘->’ (have ‘int’)
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c: In function ‘Tk_Get3DBorderFromObj’:
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1264: error: ‘TkWindow’ has no member named ‘dispPtr’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1279: error: ‘TkBorder’ has no member named ‘resourceRefCount’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1280: error: ‘Tk_FakeWin’ has no member named ‘display’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1280: error: ‘Tk_FakeWin’ has no member named ‘screenNum’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1280: error: ‘TkBorder’ has no member named ‘screen’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1281: error: ‘Tk_FakeWin’ has no member named ‘atts’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1281: error: ‘TkBorder’ has no member named ‘colormap’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1301: error: ‘TkDisplay’ has no member named ‘borderTable’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1301: error: ‘TkDisplay’ has no member named ‘borderTable’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1306: error: ‘TkBorder’ has no member named ‘nextPtr’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1307: error: ‘Tk_FakeWin’ has no member named ‘display’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1307: error: ‘Tk_FakeWin’ has no member named ‘screenNum’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1307: error: ‘TkBorder’ has no member named ‘screen’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1308: error: ‘Tk_FakeWin’ has no member named ‘atts’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1308: error: ‘TkBorder’ has no member named ‘colormap’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1311: error: ‘TkBorder’ has no member named ‘objRefCount’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c: In function ‘TkDebugBorder’:
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1391: error: ‘TkWindow’ has no member named ‘dispPtr’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1394: error: ‘TkDisplay’ has no member named ‘borderTable’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1394: error: ‘TkDisplay’ has no member named ‘borderTable’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1400: error: ‘TkBorder’ has no member named ‘nextPtr’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1403: error: ‘TkBorder’ has no member named ‘resourceRefCount’
/home/prabhakaran/Desktop/ns/tk8.4.18/unix/../generic/tk3d.c:1405: error: ‘TkBorder’ has no member named ‘objRefCount’
make: *** [tk3d.o] Error 1
tk8.4.18 make failed! Exiting ...
For problems with Tcl/Tk see [http://www.scriptics.com](http://www.scriptics.com)


---

### Post by prabhakaran1989 on 2009-05-25
i myself got recovered from that error...its just easy ...one day i tried the same step ...i got succeeded~~~!!!:))):popcorn:

---


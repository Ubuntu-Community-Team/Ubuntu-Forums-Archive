---
title: "help compileing/installing openVRML"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by monkeyslayer56 on 2009-08-14
ive been trying for awile but when i do make it jsut give me


```
josh@josh-desktop:~/openvrml-0.18.2$ make
make  all-recursive
make[1]: Entering directory `/home/josh/openvrml-0.18.2'
Making all in doc
make[2]: Entering directory `/home/josh/openvrml-0.18.2/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/josh/openvrml-0.18.2/doc'
Making all in ide-projects
make[2]: Entering directory `/home/josh/openvrml-0.18.2/ide-projects'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/josh/openvrml-0.18.2/ide-projects'
Making all in models
make[2]: Entering directory `/home/josh/openvrml-0.18.2/models'
Making all in audio
make[3]: Entering directory `/home/josh/openvrml-0.18.2/models/audio'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/josh/openvrml-0.18.2/models/audio'
Making all in textures
make[3]: Entering directory `/home/josh/openvrml-0.18.2/models/textures'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/josh/openvrml-0.18.2/models/textures'
make[3]: Entering directory `/home/josh/openvrml-0.18.2/models'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/josh/openvrml-0.18.2/models'
make[2]: Leaving directory `/home/josh/openvrml-0.18.2/models'
Making all in src
make[2]: Entering directory `/home/josh/openvrml-0.18.2/src'
make  all-recursive
make[3]: Entering directory `/home/josh/openvrml-0.18.2/src'
Making all in script
make[4]: Entering directory `/home/josh/openvrml-0.18.2/src/script'
Making all in java
make[5]: Entering directory `/home/josh/openvrml-0.18.2/src/script/java'
Making all in vrml
make[6]: Entering directory `/home/josh/openvrml-0.18.2/src/script/java/vrml'
Making all in field
make[7]: Entering directory `/home/josh/openvrml-0.18.2/src/script/java/vrml/field'
make[7]: Nothing to be done for `all'.
make[7]: Leaving directory `/home/josh/openvrml-0.18.2/src/script/java/vrml/field'
Making all in node
make[7]: Entering directory `/home/josh/openvrml-0.18.2/src/script/java/vrml/node'
make[7]: Nothing to be done for `all'.
make[7]: Leaving directory `/home/josh/openvrml-0.18.2/src/script/java/vrml/node'
make[7]: Entering directory `/home/josh/openvrml-0.18.2/src/script/java/vrml'
make[7]: Nothing to be done for `all-am'.
make[7]: Leaving directory `/home/josh/openvrml-0.18.2/src/script/java/vrml'
make[6]: Leaving directory `/home/josh/openvrml-0.18.2/src/script/java/vrml'
make[6]: Entering directory `/home/josh/openvrml-0.18.2/src/script/java'
cvf script.jar vrml/InvalidEventInException.class vrml/InvalidEventOutException.class vrml/InvalidExposedFieldException.class vrml/InvalidFieldChangeException.class vrml/InvalidFieldException.class vrml/InvalidRouteException.class vrml/InvalidVRMLSyntaxException.class vrml/Browser.class vrml/Event.class vrml/Field.class vrml/ConstMField.class vrml/MField.class vrml/ConstField.class vrml/BaseNode.class vrml/field/SFBool.class vrml/field/SFColor.class vrml/field/SFFloat.class vrml/field/SFImage.class vrml/field/SFInt32.class vrml/field/SFNode.class vrml/field/SFRotation.class vrml/field/SFString.class vrml/field/SFTime.class vrml/field/SFVec2f.class vrml/field/SFVec3f.class vrml/field/MFBool.class vrml/field/MFColor.class vrml/field/MFFloat.class vrml/field/MFInt32.class vrml/field/MFNode.class vrml/field/MFRotation.class vrml/field/MFString.class vrml/field/MFTime.class vrml/field/MFVec2f.class vrml/field/MFVec3f.class vrml/field/ConstSFBool.class vrml/field/ConstSFColor.class vrml/field/ConstSFFloat.class vrml/field/ConstSFImage.class vrml/field/ConstSFInt32.class vrml/field/ConstSFNode.class vrml/field/ConstSFRotation.class vrml/field/ConstSFString.class vrml/field/ConstSFTime.class vrml/field/ConstSFVec2f.class vrml/field/ConstSFVec3f.class vrml/field/ConstMFBool.class vrml/field/ConstMFColor.class vrml/field/ConstMFFloat.class vrml/field/ConstMFInt32.class vrml/field/ConstMFNode.class vrml/field/ConstMFRotation.class vrml/field/ConstMFString.class vrml/field/ConstMFTime.class vrml/field/ConstMFVec2f.class vrml/field/ConstMFVec3f.class vrml/field/SFVec2d.class vrml/field/ConstSFVec2d.class vrml/field/ConstMFVec2d.class vrml/field/SFDouble.class vrml/field/MFDouble.class vrml/field/ConstSFDouble.class vrml/field/ConstMFDouble.class vrml/field/SFVec3d.class vrml/field/ConstSFVec3d.class vrml/field/ConstMFVec3d.class vrml/node/Node.class vrml/node/Script.class
/bin/bash: cvf: command not found
make[6]: *** [script.jar] Error 127
make[6]: Leaving directory `/home/josh/openvrml-0.18.2/src/script/java'
make[5]: *** [all-recursive] Error 1
make[5]: Leaving directory `/home/josh/openvrml-0.18.2/src/script/java'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/josh/openvrml-0.18.2/src/script'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/josh/openvrml-0.18.2/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/josh/openvrml-0.18.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/josh/openvrml-0.18.2'
make: *** [all] Error 2

```
any ideas on what to do? i am pritty sure ive installed all the dependencies but i may have missed one. if anyone can help me please do

---

### Post by pivotter on 2009-11-26
you can check 1.8.3 on debian sid for the list of required packages
[http://packages.debian.org/source/sid/openvrml](http://packages.debian.org/source/sid/openvrml)

pivotter

---

### Post by Mugiwara no Tapir on 2010-07-27
hi 

try this:

./configure --disable-script-node-javascript --disable-mozilla-plugin
make
sudo make install

you need install "Boost library"

---


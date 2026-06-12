---
title: "Trouble forwarding netbackup java console over x from linux box"
date: 2005-11-04
forum: General Help
---

### Post by jlo on 2005-11-04
I am trying to forward the Netbackup Java Admin Console from a box running Redhat back to my ubuntu laptop and receive the following error:

java.lang.InternalError: Can't connect to X11 window server using 'rockin:0.0' as the value of the DISPLAY variable.
        at sun.awt.X11GraphicsEnvironment.initDisplay(Native Method)
        at sun.awt.X11GraphicsEnvironment.<clinit>(X11GraphicsEnvironment.java:126)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:130)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:62)
        at java.awt.Window.init(Window.java:224)
        at java.awt.Window.<init>(Window.java:268)
        at java.awt.Frame.<init>(Frame.java:398)
        at javax.swing.JFrame.<init>(JFrame.java:198)
        at vrts.common.utilities.CommonFrame.<init>(CommonFrame.java:58)
        at vrts.common.utilities.CommonFrame.<init>(CommonFrame.java:53)
        at vrts.nbe.JavaPresentationLayer.<init>(JavaPresentationLayer.java:56)
        at vrts.nbe.AdminConsole.<init>(AdminConsole.java:44)
        at vrts.nbe.AdminConsole.main(AdminConsole.java:91)

I have run xhost + on my laptop and set the Display variable as export DISPLAY=rockin:0.0

Any ideas what i am doing wrong here?

---

### Post by jlo on 2005-11-04
Ok, so i solved this one on my own.
Basically forwarded x connections are blocked in the default installation. In order to allow x forwarding from remote hosts:

System->Administration->LoginScreenSetup
Choose the security tab and uncheck deny TCP connections to xserver. 
Logout and Log back in.
This should enable xforwarding to your machine.

peace

---


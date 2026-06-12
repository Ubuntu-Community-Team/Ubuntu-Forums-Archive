---
title: "Java Swing/AWT thread problem"
date: 2008-08-14
forum: General Help
---

### Post by tvandrunen on 2008-08-14
We've recently switched to Ubuntu in our studen laboratory, and we're having a strange issue with Java applications that use Swing/AWT. It seems that threads waiting for certain events (for example, a window being closed) never get woken up. However, after making a mutation to the code that should be irrelevant (for example, having the thread make dummy output to the screen while waiting), suddenly the code works. Sample code exhibiting the problem is included below.

We're running Ubuntu 8.04, and our java version is

java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Server VM (build 10.0-b22, mixed mode)

If this inquiry is better suited to another forum, please direct us there. Thanks so much.



In the code example below, a window with a button pops up. When the button is pressed, the first window disappears and a second window comes up. The problem we're seeing is that the second window never appears. We've found that this program works on the following systems:

A NETBSD machine running Java 1.5
A MacOS machine running Java 1.5
A Windows machine running Java 1.6u7


import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class SwingTest {

    public static void main(String[] args) {

        final JFrame window1 = new JFrame();
        window1.setSize(100, 100);
        window1.setLocation(100, 100);
        JButton jbutt = new JButton("Click here");
        window1.add(jbutt);
        window1.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        jbutt.addActionListener(new ActionListener() {
                public void actionPerformed(ActionEvent ae) {
                    window1.setVisible(false);
                }
            });

        window1.setVisible(true);

        // option 1: doesn't work (the second window never appears)
        while (window1.isVisible()) ;

        // option 2: works correctly
        // while (window1.isVisible()) System.out.println(".");

        JFrame window2 = new JFrame();
        window2.setSize(100, 100);
        window2.setLocation(200, 200);
        window2.add(new JLabel("ok"));
        window1.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        window2.setVisible(true);

    }
}

---

### Post by txcrackers on 2008-08-14
> while (window1.isVisible()) ;
This causes the application to "spin" at this point and not do anything else. Remove this line, **and** the other while loop. They are not needed and all they do is eat up CPU processing needlessly.

---

### Post by tvandrunen on 2008-08-14
I understand what the loop does and that my example isn't exactly efficient. But that's not the point. It should still work (ie, the loop should break when the first window is closed). It appears that the spinning main thread is being put to sleep and not woken up.

Thanks

Tom

---


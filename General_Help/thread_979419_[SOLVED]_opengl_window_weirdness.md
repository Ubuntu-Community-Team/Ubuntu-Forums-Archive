---
title: "[SOLVED] opengl window weirdness"
date: 2008-11-11
forum: General Help
---

### Post by bla687 on 2008-11-11
I've been working with opengl on another computer running red hat, and now I'm trying to run it on my computer running ubuntu 8.10. The window opens fine on the other computer, but on mine when opengl opens a window to display the rendered scene, I can see it for a little less than a second and then it disappears. It still shows up on the panel, and the compiz window preview shows the correct contents of the window (or it used to, I don't have that effect enabled any more), but the window is invisible. I'm using the ati proprietary drivers, and the window is opened with the following code:

  glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGBA | GLUT_ALPHA | GLUT_DEPTH);
  glutInitWindowSize(WIDTH, HEIGHT); 
  glutInitWindowPosition(100, 100);
  glutCreateWindow(argv[0]);

Any ideas for fixing this problem?

edit: Just some additional information: I'm using the restricted ati drivers and I have a radeon x1600xt video card. I've found the image only displays when the image is drawn/redrawn. The window is definitely there because I can use my mouse callback functions to rotate and zoom the scene, so I can view the image by keeping a mouse button held down and moving it around, but it's kind of annoying.

Well, the problem was desktop effects. I completely disabled them, and now it works perfectly.

---


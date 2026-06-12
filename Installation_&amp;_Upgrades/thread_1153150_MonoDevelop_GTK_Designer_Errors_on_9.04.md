---
title: "MonoDevelop GTK Designer Errors on 9.04"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by N3X15 on 2009-05-08
I upgraded to Ubuntu 9.04 yesterday, and most everything has gone smoothly.  However, I have run into a brick wall, as a project I was working on with MonoDevelop is now completely messed up since the GTK# GUI designer no longer works as it should.  The project revolves around converting a Winforms application (with a LOT of forms) to GTK#, which makes it impractical to manually code every bloody form.

When opening up any gtk# form (even a brand new one) in the designer, I receive the following unhandled exception:

```

System.ArgumentNullException: Argument cannot be null.
Parameter name: path
  at MonoDevelop.Core.FileService.GetFullPath (System.String path) [0x00000] 
  at MonoDevelop.GtkCore.GuiBuilder.ToolboxProvider.GetDynamicItems (IToolboxConsumer consumer) [0x00000] 
  at MonoDevelop.DesignerSupport.ToolboxService.GetToolboxItems (IToolboxConsumer consumer) [0x00000] 
  at MonoDevelop.DesignerSupport.ToolboxService.GetCurrentToolboxItems () [0x00000] 
  at MonoDevelop.DesignerSupport.Toolbox.Toolbox.Refresh () [0x00000] 
  at MonoDevelop.DesignerSupport.Toolbox.Toolbox+<Toolbox>c__AnonStorey10.<>m__10 (System.Object , MonoDevelop.DesignerSupport.ToolboxConsumerChangedEventArgs ) [0x00000] 
  at MonoDevelop.DesignerSupport.ToolboxService.OnToolboxConsumerChanged (IToolboxConsumer consumer) [0x00000] 
  at MonoDevelop.DesignerSupport.ToolboxService.set_CurrentConsumer (IToolboxConsumer value) [0x00000] 
  at MonoDevelop.DesignerSupport.ToolboxService.OnViewChanged (System.Object sender, System.EventArgs args) [0x00000] 
  at MonoDevelop.Ide.Gui.Document.OnViewChanged (System.EventArgs args) [0x00000] 
  at MonoDevelop.Ide.Gui.Document.OnActiveViewContentChanged (System.Object s, System.EventArgs args) [0x00000] 
  at MonoDevelop.Ide.Gui.SdiWorkspaceWindow.OnActiveViewContentChanged (MonoDevelop.Ide.Gui.ActiveViewContentEventArgs e) [0x00000] 
  at MonoDevelop.Ide.Gui.SdiWorkspaceWindow.set_ActiveViewContent (IBaseViewContent value) [0x00000] 
  at MonoDevelop.GtkCore.GuiBuilder.CombinedDesignView+<CombinedDesignView>c__AnonStorey2.<>m__3 (System.Object , Gtk.SwitchPageArgs ) [0x00000] 
  at Gtk.Notebook.SwitchPageSignalCallback (IntPtr arg0, IntPtr arg1, UInt32 arg2, IntPtr gch) [0x00000] 

```

The following appears in the console when running from terminal:

```

$ monodevelop
WARNING: Cannot find Mozilla directory containing libgtkembedmoz.so. Some Addins may not be able to function. Please set MOZILLA_FIVE_HOME to your Mozilla directory.
node `embed' is not defined on the documentation map
PARSE LOAD: 159.02

```

I've tried completely reinstalling monodevelop via synaptic, and that got me nowhere.

I operate on an Intel Core Duo (3.0Ghz) with 4.0GB System RAM using an nVidia GeForce 8800 GTS.  I am using the i686 distribution of Ubuntu.

Any suggestions to get this working?

---

### Post by N3X15 on 2009-05-08
Update:  Seems to have automagically resolved the problem itself after a few hours, which is odd as I haven't touched it...  Designed forms don't have a titlebar, but whatever.

---

### Post by iKevin on 2009-06-17
I am having this same issue on to ubuntu boxes.  Can you describe more about the updates?  I applied all updates up to Jun 17.

---


# NonInvasiveKeyboardHook
A C# hotkey manager that uses a low level global hook, but allows registering for specific keys to reduce invasion of user privacy.

### Get it on NuGet
https://www.nuget.org/packages/NonInvasiveKeyboardHookLibrary/



### Example
```csharp
var keyboardHookManager = new KeyboardHookManager();
keyboardHookManager.Start();

// Register virtual key code 0x60 = NumPad0
keyboardHookManager.RegisterHotkey(0x60, () =>
{
    Debug.WriteLine("NumPad0 detected");
});

// Modifiers are supported too
keyboardHookManager.RegisterHotkey(NonInvasiveKeyboardHookLibrary.ModifierKeys.Control, 0x60, () => 
{ 
    Debug.WriteLine("Ctrl+NumPad0 detected");
});

// Multiple modifiers can be specified using the bitwise OR operation
keyboardHookManager.RegisterHotkey(NonInvasiveKeyboardHookLibrary.ModifierKeys.Control | NonInvasiveKeyboardHookLibrary.ModifierKeys.Alt, 0x60, () => 
{ 
    Debug.WriteLine("Ctrl+Alt+NumPad0 detected");
});

// Or as an array of modifiers
keyboardHookManager.RegisterHotkey(new[]{NonInvasiveKeyboardHookLibrary.ModifierKeys.Control, NonInvasiveKeyboardHookLibrary.ModifierKeys.Alt}, 0x60, () =>
{
    Debug.WriteLine("Ctrl+Alt+NumPad0 detected");
});
```

For more code examples, look at the example project: https://github.com/kfirprods/ShortcutHotkeysExample

For a thorough explanation, look at the CodeProject article: https://www.codeproject.com/Articles/1273010/Global-Hotkeys-within-Desktop-Applications

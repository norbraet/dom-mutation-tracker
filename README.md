# DOM Mutation Tracker

🔍 A lightweight JavaScript utility that tracks DOM mutations in real-time, providing clean console logging and visual highlighting of changed elements.

![Chrome DevTools Compatible](https://img.shields.io/badge/Chrome%20DevTools-Compatible-green)
![No Dependencies](https://img.shields.io/badge/Dependencies-None-blue)
![Pure JavaScript](https://img.shields.io/badge/Language-JavaScript-yellow)

## ✨ Features

- **🎯 Real-time DOM Monitoring** - Tracks all DOM changes as they happen
- **🎨 Visual Highlighting** - Changed elements flash red for easy identification
- **📊 Clean Console Logging** - Organized, collapsible console output
- **🔍 Multiple Mutation Types** - Tracks attributes, child nodes, and text changes
- **🛡️ Loop Prevention** - Intelligent filtering to avoid infinite loops
- **⚡ Zero Dependencies** - Pure JavaScript, no external libraries
- **🎮 Interactive API** - Simple functions to control tracking

## 🚀 Quick Start

### Chrome DevTools Snippet (Recommended)

1. **Open Chrome DevTools** (`F12` or `Ctrl+Shift+I`)
2. **Go to Sources tab** → **Snippets** (left sidebar)
3. **Create new snippet** → Name it `dom-mutation-tracker`
4. **Copy and paste** the entire `dom-mutation-tracker.js` content
5. **Run the snippet** (`Ctrl+Enter` or `Righclick + Run`)

### Alternative Usage

```javascript
// Include in your HTML
<script src="dom-mutation-tracker.js"></script>;

// Or load dynamically
fetch("dom-mutation-tracker.js")
  .then((response) => response.text())
  .then((script) => eval(script));
```

## 📋 Usage Examples

### Basic Usage

```javascript
// Tracking starts automatically when loaded
// Watch the console for mutation logs!

// Manual control
stopMutationTracker(); // Stop tracking
startMutationTracker(); // Resume tracking
```

### API Reference

| Function                 | Description                            |
| ------------------------ | -------------------------------------- |
| `startMutationTracker()` | Start/resume DOM mutation tracking     |
| `stopMutationTracker()`  | Stop tracking and cleanup              |
| `getMutationLog()`       | View all recorded mutations in console |
| `clearMutationLog()`     | Clear the mutation history             |

### Console Output Examples

```
🔧 class → button.primary     // Attribute change
➕ Added → div.container       // Child nodes added
➖ Removed → ul.list          // Child nodes removed
📝 Text → span "Hello..."      // Text content changed
```

## ⚙️ Configuration

Customize the tracker by modifying the `CONFIG` object:

```javascript
const CONFIG = {
  highlightColor: "#ff0000", // Highlight color (red)
  highlightDuration: 3000, // How long to highlight (3s)
  maxLogEntries: 100, // Maximum logged mutations
  debounceTime: 50, // Duplicate filtering (50ms)
  highlightClassName: "mutation-tracker-highlight",
};
```

## 🎯 What Gets Tracked

### Attribute Changes

- Class modifications
- Style changes
- Data attributes
- ID changes
- Any attribute modification

**Example Output:**

```
🔧 style → div.modal
  Element: <div class="modal">
  Attribute: style
  Old: display: none
  New: display: block
  Time: 14:23:15
```

### Child Node Changes

- Elements added to DOM
- Elements removed from DOM
- Text nodes inserted/removed

**Example Output:**

```
➕ Added → ul.menu
  Parent: <ul class="menu">
  Added: [<li>New Item</li>]
  Time: 14:23:16
```

### Text Content Changes

- Text node modifications
- innerHTML changes affecting text

**Example Output:**

```
📝 Text → span "Loading complete"
  Text Node: #text
  Parent: <span class="status">
  Old: "Loading..."
  New: "Loading complete"
  Time: 14:23:17
```

## 🛠️ Common Use Cases

### Debugging Dynamic Content

```javascript
// Perfect for tracking:
// - React/Vue component updates
// - AJAX content loading
// - Animation state changes
// - Form validation feedback
```

### Performance Analysis

```javascript
// Monitor excessive DOM modifications
startMutationTracker();
// ... perform actions ...
const log = getMutationLog();
console.log(`Total mutations: ${log.length}`);
```

### Development Workflow

```javascript
// In Chrome DevTools Console:
startMutationTracker();
// Click buttons, interact with page
// Watch mutations in real-time!
stopMutationTracker();
```

## 🔧 Troubleshooting

### High Mutation Count

If you see too many mutations:

- Increase `debounceTime` in config
- Check for infinite loops in your code
- Look for excessive style recalculations

### Missing Mutations

- Ensure tracking is active: check console for "DOM Mutation Tracker Started"
- Some mutations might be filtered as duplicates
- Check if mutations happen outside `document.body`

### Performance Impact

- Tracking adds minimal overhead
- Stop tracking when not needed: `stopMutationTracker()`
- Limit `maxLogEntries` for long sessions

## 🚫 Limitations

- Only tracks mutations within `document.body`
- Doesn't track mutations in iframes
- Doesn't track mutations in CSS, otherwise the element hightlighting would retrigger the observer
- Limited to modern browsers supporting `MutationObserver`
- Large numbers of rapid mutations may impact performance

## 🌐 Browser Compatibility

- ✅ Chrome/Chromium (all recent versions)
- ✅ Firefox (all recent versions)
- ✅ Safari (all recent versions)
- ✅ Edge (all recent versions)
- ❌ Internet Explorer (not supported)

## 🤝 Contributing

Contributions are welcome! Please feel free to:

- Report bugs
- Suggest features
- Submit pull requests
- Improve documentation

## 📄 License

This project is released under the MIT License. Feel free to use it in personal and commercial projects.

## 🙏 Acknowledgments

- Built using the native `MutationObserver` API
- Inspired by the need for better DOM debugging tools
- Designed for Chrome DevTools workflow

---

**Happy DOM debugging! 🚀**

_Found this useful? Give it a ⭐ and share with fellow developers!_

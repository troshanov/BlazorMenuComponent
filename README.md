# Blazor Menu Component

This project implements a hierarchical menu component for Blazor applications. The menu supports infinite nesting of menu items and dynamically displays submenus on hover.

## Project Structure

- **Progress.Sample.App.Components**: A class library containing the reusable menu components
- **Progress.Sample.App**: A Blazor WebAssembly application demonstrating the use of the menu components

## Features

1. **Hierarchical Menu Structure**: Support for top-level (root) and child items with unlimited nesting depth
2. **Hover-Based Submenu Display**: Submenus appear when hovering over parent menu items
3. **Submenu Positioning**: First-level submenus display below the parent, deeper submenus display to the right
4. **Automatic Submenu Closing**: Submenus close when the mouse moves outside of them
5. **Event Handling (Bonus)**: Support for item click events

## Implementation Choices

### Component Structure

I chose to implement the menu system using three main components:

1. **Menu**: The root container for the entire menu system
2. **MenuItems**: A collection component for grouping menu items
3. **MenuItem**: The individual menu item component with hover capability

This structure allows for a clean, declarative syntax when defining menus in Razor files. The nesting capability is achieved through the use of `RenderFragment` parameters that allow child content to be passed to parent components. Also, I've implemented conditional rendering for the submenus - they are only rendered upon hover over their parent. For deeply nested menus with many items, this can significantly improve performance since only the actively hovered parts of the menu hierarchy are in the DOM.

### State Management

I used a combination of local component state and cascading parameters to manage the menu system:

- **Local State**: Each `MenuItem` manages its own hover state
- **Cascading Parameters**: Used to communicate whether a menu item is part of a submenu, which affects its rendering behavior

### Event Handling

Mouse events (enter/leave/click) are used to control submenu visibility and invoke assigned callbacks.

## Running the Project
1. Set the `Progress.Sample.App` project as the startup project
2. Run the application
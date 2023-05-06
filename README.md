# bind_focus_state_with_child_view

```swift
struct Parent: View {
    @FocusState var focusedField: UUID?
     
    var body: some View {
        VStack {
            Child(focusedField: $focusedField)
            Sibling(focusedField: $focusedField)
        }
    }
}
struct Child: View {
    var focusedField: FocusState<UUID?>.Binding
    @State var someText: String = ""
    @State var someTextFieldUUID: UUID = UUID()    

    var body: some View {
        VStack {
            TextField("Focusable field", text: $someText)
                 .focused(focusedField, equals: someTextFieldUUID)
        }
    }
}
```

```swift
struct Parent: View {
    @FocusState var focusedField: UUID?
     
    var body: some View {
        VStack {
            Child(focusedField: _focusedField)
        }
    }
}
struct Child: View {
    @FocusState var focusedField: UUID?
    @State var someText: String = ""
    @State var someTextFieldUUID: UUID = UUID()    

    var body: some View {
        VStack {
            TextField("Focusable field", text: $someText)
                 .focused($focusedField, equals: someTextFieldUUID)
        }
    }
}
```

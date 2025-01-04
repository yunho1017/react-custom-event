# react-custom-event
Define your own custom events in react !

## Introduction

Let's implement a dialog using React.

The dialog has inputs. if values ​​are entered in the inputs, leave alert should be displayed when closing the dialog.

In this case, How would you implement this?

There are several ways to solve this. You can use ref or manage the values ​​on the side that declares the dialog.

How about this?

```js

const DialogCloseEvent = createCustomEvent("dialog-close");

const Dialog = (props) => {
  return <Modal {...props} onClose={()=> {
  try {
  DialogCloseEvent.call()
  props.onClose()
}
}>
{props.children}
</Modal>
}

const Component = () => {
  const [state, setState] = useState()
  useEffect(() => {
  const handler = () => {
if (state) {
throw new Error("leaveAlert!")
openLeaveAlert()
}
}


DialogCloseEvent.addEventListener(handler)
  return () => {
DialogCloseEvent.removeEventListener(handler)
}
},[])
  return <Componet1/>
}


```

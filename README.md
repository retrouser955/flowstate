# FlowState

Create programs using a visual language

### THIS LIBRARY IS STILL IN DEVELOPMENT AND WILL NOT WORK

## Concept

```ts
import { FlowStateWorkspace } from "@flowstate/core"
import { loadDefaultNodes } from "@flowstate/basenodes"

const workspace = new FlowStateWorkspace("element")
workspace.addNodes(loadDefaultNodes())
```

### Custom Nodes

```ts
import { NodeBuilder, InputType, OutputType } from "@flowstate/core"

const myNode = new NodeBuilder()
.setID("com.retrouser955.flowstate.maths.add")
.setDisplayName("Add numbers")
.addInput((options) => {
    return options
        .setID("num1")
        .setType(InputType.Number)
})
.addInput((options) => {
    return options
        .setID("num2")
        .setType(InputType.Number)
})
.addOutput((options) => {
    return options
        .setID("results")
        .setType(OutputType.Number)
})
.defineCodeGen((ctx) => {
    const [input1, input2] = [ctx.getInput("num1"), ctx.getInput("num2")]
    return `${input1 + input2}`
})
.build()

workspace.addNode(myNode)
```
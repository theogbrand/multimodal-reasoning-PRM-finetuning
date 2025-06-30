!-- ---
layout: default
---

# RL to Improve Policy Model, and Using PRM at Test-Time

```mermaid
graph LR
    Input[Image + Query] --> Policy[Policy Model]
    Policy --> |Generates| R1[Reasoning Step 1]
    R1 --> PRM1[PRM Evaluation]
    PRM1 --> |Feedback| R2[Reasoning Step 2]
    R2 --> PRM2[PRM Evaluation]
    PRM2 --> |Feedback| R3[...]
    R3 --> Final[Final Answer]
    
    PRM[Process Reward Model] -.-> PRM1
    PRM -.-> PRM2
    
    subgraph RL[RL Training Loop]
      PRM --> |Rewards| Update[Policy Update]
      Update --> Policy
      Experience[Experience Collection] --> Update
      Policy -.-> Experience
    end
    
    style Input fill:#def,stroke:#333,color:black
    style Policy fill:#ff9,stroke:#333,color:black
    style R1 fill:#bfa,stroke:#333,color:black
    style R2 fill:#bfa,stroke:#333,color:black
    style R3 fill:#bfa,stroke:#333,color:black
    style Final fill:#ffb86c,stroke:#333,color:black
    style PRM fill:#9cf,stroke:#333,color:black
    style PRM1 fill:#9cf,stroke:#333,color:black
    style PRM2 fill:#9cf,stroke:#333,color:black
    style Update fill:#f99,stroke:#333,color:black
    style Experience fill:#d8f,stroke:#333,color:black
    style RL fill:none,stroke:#f55,stroke-width:2px,color:black,stroke-dasharray: 5 5
```

## Value Add of PRMs

- PRM provides **real-time feedback** during inference
- Guides the policy model to generate **high-quality reasoning traces**
- Enables **test-time scaling** without additional training
- Results in more **reliable and interpretable** multimodal reasoning
- **RL training loop** uses PRM rewards to continuously improve policy model -->